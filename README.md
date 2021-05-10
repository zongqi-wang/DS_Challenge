# Fall 2021 Data Science Intern Challenge

## QUESTION 1

### (a)
There are 5000 sales in total, 71 of which have an order amount greater than 1000 and 57 of which are greater than 10000. There is a single user, id 607, who has bought 2000 sneakers totaling 704000 seventeen times in total skewing the results. In addition, all transactions totaling over 10000 dollars are spent in 2 stores (id 42, and 78). Store 42 seems to sell only reasonably priced sneakers but has an extremely valuable customer who buys 2000 sneakers at a time, but store 78 only sells expensive shoes no less than 25k in price.

There are 2 ways to evaluate this data. The simplest way is to use the median value ($284) instead of mean value (3145.13) to evaluate AOV. Or we can remove the outliers, specifically the customer who buys 2000 sneakers at once and the store that only sells expensive sneakers. After removing the shop and the customer, the AOV comes down to ($302.58), a reasonable amount.

### (b)
For this dataset, since we are only given one month data and a limited number of features, there are few metrics we can calculate. For instance, we can track how well a store is doing by calculating its AOV and the number of transactions. Check if a store needs to spend money to maintain credit card payments by checking payment methods. 

Check the users’ spending habits, such as average number of sneakers they buy per month, and their average value. Do they use credit cards or cash? Do they travel to other stores to buy or stick to one store? 

If we continued to collect data, we would be able to track sales histories, such as sales growth of store, conversion rates of stores by checking if customers changed stores. If we had product ID we could track product sales performance. If we had location data of the shop we could track region performance and better understand customer conversion.

### (c)
The value of this data set is that it allows us to model sales and predict future sales as to prevent overstocking.


## Question 2
### (a)
```
  SELECT COUNT(*) FROM Orders  
  INNER JOIN Shippers  
  ON Orders.ShipperID = Shippers.ShipperID  
  WHERE Shippers.ShipperName = "Speedy Express"  
```

__54__


### (b)
```
  SELECT Employees.LastName FROM Orders  
  INNER JOIN Employees  
  ON Orders.EmployeeID = Employees.EmployeeID  
  GROUP BY Orders.EmployeeID  
  HAVING count(*) > 1  
  ORDER BY count(*) DESC  
  LIMIT 1  
```


__Peacock__

### (c)
```
SELECT ProductName FROM  
(SELECT * FROM Orders  
INNER JOIN OrderDetails  
ON Orders.OrderID = OrderDetails.OrderID  
INNER JOIN Products  
ON OrderDetails.ProductID = Products.ProductID  
INNER JOIN Customers  
ON Orders.CustomerID = Customers.CustomerID  
Where Customers.Country = "Germany") t1  
GROUP BY ProductID  
HAVING COUNT(*) > 1  
ORDER BY COUNT(*) DESC  
LIMIT 1
```

__Gorgonzola Telino__

