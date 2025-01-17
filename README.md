# Telecom Inventory Management System
Database
1. Search Products by Name
Search for products where the name contains a specific keyword (e.g., "Router").

sql
Copy code
SELECT * 
FROM Products
WHERE name LIKE '%Router%';
2. Search Products by Category
Search for products belonging to a specific category (e.g., "Networking").

sql
Copy code
SELECT * 
FROM Products
WHERE category = 'Networking';
3. Search Products by Stock Level
Search for products with a specific stock level (e.g., 50 units).

sql
Copy code
SELECT * 
FROM Products
WHERE stock_level = 50;
4. Filter Products: Low Stock
Retrieve products where the stock level is below the reorder point (indicating low stock).

sql
Copy code
SELECT * 
FROM Products
WHERE stock_level < reorder_point;
5. Filter Products: Out of Stock
Retrieve products that are completely out of stock.

sql
Copy code
SELECT * 
FROM Products
WHERE stock_level = 0;
6. Combined Search and Filter
Search for products by name and filter by low stock.

sql
Copy code
SELECT * 
FROM Products
WHERE name LIKE '%Router%' AND stock_level < reorder_point;
7. Filter by Multiple Stock Statuses
Retrieve products based on their stock status (e.g., low stock and out of stock).

sql
Copy code
SELECT *, 
       CASE 
           WHEN stock_level = 0 THEN 'Out of Stock'
           WHEN stock_level < reorder_point THEN 'Low Stock'
           ELSE 'In Stock'
       END AS stock_status
FROM Products
WHERE stock_level = 0 OR stock_level < reorder_point;
8. Sort Results
Sort the results of any search or filter query by a specific column, such as name or stock_level.

Sort by Name (Ascending):

sql
Copy code
SELECT * 
FROM Products
ORDER BY name ASC;
Sort by Stock Level (Descending):

sql
Copy code
SELECT * 
FROM Products
ORDER BY stock_level DESC;
9. Pagination for Search and Filtering
For large datasets, paginate the results to show a limited number of rows per page (e.g., 10 rows per page).

sql
Copy code
SELECT * 
FROM Products
WHERE name LIKE '%Router%'
ORDER BY name ASC
LIMIT 10 OFFSET 0; -- Page 1 (Rows 1-10)
Change OFFSET for other pages:

Page 2: OFFSET 10
Page 3: OFFSET 20, etc.
