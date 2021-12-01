# SQLExamples


# What is SQL?
SQL stands for Structured Query Language
SQL lets you access and manipulate databases
SQL became a standard of the American National Standards Institute (ANSI) in 1986, and of the International Organization for Standardization (ISO) in 1987


The data in RDBMS is stored in database objects called tables. A table is a collection of related data entries and it consists of columns and rows.

# What Can SQL do?
SQL can execute queries against a database
SQL can retrieve data from a database
SQL can insert records in a database
SQL can update records in a database
SQL can delete records from a database
SQL can create new databases
SQL can create new tables in a database
SQL can create stored procedures in a database
SQL can create views in a database
SQL can set permissions on tables, procedures, and views



Database Tables

CustomerID	   CustomerName	              ContactName	                    Address	            City	              PostalCode	     Country
1	             Alfreds Futterkiste	      Maria Anders	                    Obere Str. 57	    Berlin	                12209	       Germany
2	             Ana Trujillo Emparedados y helados	Ana Trujillo	           Avda. de la Constitución 2222	México D.F.	              05021	      Mexico


# SQL Statements
Most of the actions you need to perform on a database are done with SQL statements.

SQL keywords are NOT case sensitive: select is the same as SELECT


The following SQL statement selects all the records in the "Customers" table:
Some of The Most Important SQL Commands
SELECT - extracts data from a database
UPDATE - updates data in a database
DELETE - deletes data from a database
INSERT INTO - inserts new data into a database
CREATE DATABASE - creates a new database
ALTER DATABASE - modifies a database
CREATE TABLE - creates a new table
ALTER TABLE - modifies a table
DROP TABLE - deletes a table
CREATE INDEX - creates an index (search key)
DROP INDEX - deletes an index

The following SQL statement selects all the records in the "Customers" table:

# SELECT and DISTINCT


SELECT * FROM Customers; 


The following SQL statement selects the "CustomerName" and "City" columns from the "Customers" table:

SELECT CustomerName,City FROM Customers;

The following SQL statement selects all (including the duplicates) values from the "Country" column in the "Customers" table:

SELECT Country FROM Customers;


The following SQL statement selects only the DISTINCT values from the "Country" column in the "Customers" table:

SELECT DISTINCT Country FROM Customers;


The following SQL statement lists the number of different (distinct) customer countries:

SELECT COUNT(DISTINCT Country) FROM Customers;

# WHERE STATEMENTS

The following SQL statement selects all the customers from the country "Mexico", in the "Customers" table:

SELECT * FROM Customers
WHERE Country='Mexico';

# Text Fields vs. Numeric Fields
SQL requires single quotes around text values (most database systems will also allow double quotes).

However, numeric fields should not be enclosed in quotes:

SELECT * FROM Customers
WHERE CustomerID=1;

Operator	Description	Example
=	Equal	
>	Greater than	
<	Less than	
>=	Greater than or equal	
<=	Less than or equal	
<>	Not equal. Note: In some versions of SQL this operator may be written as !=	
BETWEEN	Between a certain range	
LIKE	Search for a pattern	
IN	To specify multiple possible values for a column


#  The SQL AND, OR and NOT Operators


The following SQL statement selects all fields from "Customers" where country is "Germany" AND city is "Berlin":

SELECT * FROM Customers
WHERE Country='Germany' AND City='Berlin';

The following SQL statement selects all fields from "Customers" where city is "Berlin" OR "München":

SELECT * FROM Customers
WHERE City='Berlin' OR City='München';

The following SQL statement selects all fields from "Customers" where country is NOT "Germany" and NOT "USA":

SELECT * FROM Customers
WHERE NOT Country='Germany' AND NOT Country='USA';

#   The SQL ORDER BY Keyword

The following SQL statement selects all customers from the "Customers" table, sorted by the "Country" column:


SELECT * FROM Customers
ORDER BY Country;


The following SQL statement selects all customers from the "Customers" table, sorted DESCENDING by the "Country" column:

SELECT * FROM Customers
ORDER BY Country DESC;

The following SQL statement selects all customers from the "Customers" table, sorted by the "Country" and the "CustomerName" column. This means that it orders by Country, but if some rows have the same Country, it orders them by CustomerName:

SELECT * FROM Customers
ORDER BY Country, CustomerName;

The following SQL statement selects all customers from the "Customers" table, sorted ascending by the "Country" and descending by the "CustomerName" column:

SELECT * FROM Customers
ORDER BY Country ASC, CustomerName DESC;



#   The SQL INSERT INTO Statement

INSERT INTO Customers (CustomerName, ContactName, Address, City, PostalCode, Country)
VALUES ('Cardinal', 'Tom B. Erichsen', 'Skagen 21', 'Stavanger', '4006', 'Norway');#^


#   The SQL Null Statement

A field with a NULL value is a field with no value.

IS NULL Syntax:

SELECT column_names
FROM table_name
WHERE column_name IS NULL;

IS NOT NULL Syntax:

SELECT column_names
FROM table_name
WHERE column_name IS NOT NULL;

The following SQL lists all customers with a NULL value in the "Address" field:

SELECT CustomerName, ContactName, Address
FROM Customers
WHERE Address IS NULL;

#   The SQL Update Statement
The UPDATE statement is used to modify the existing records in a table.

UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;

Note: Be careful when updating records in a table! Notice the WHERE clause in the UPDATE statement. The WHERE clause specifies which record(s) that should be updated. If you omit the WHERE clause, all records in the table will be updated!

UPDATE Table:
The following SQL statement updates the first customer (CustomerID = 1) with a new contact person and a new city.


UPDATE Customers
SET ContactName = 'Alfred Schmidt', City= 'Frankfurt'
WHERE CustomerID = 1;

UPDATE Multiple Records
The following SQL statement will update the ContactName to "Juan" for all records where country is "Mexico":

UPDATE Customers
SET ContactName='Juan'
WHERE Country='Mexico';

Be careful when updating records. If you omit the WHERE clause, ALL records will be updated!



#   The SQL DELETE Statement

The following SQL statement deletes the customer "Alfreds Futterkiste" from the "Customers" table:

DELETE FROM Customers WHERE CustomerName='Alfreds Futterkiste';

Delete All Records
It is possible to delete all rows in a table without deleting the table. This means that the table structure, attributes, and indexes will be intact:

DELETE FROM table_name;

# The SQL SELECT TOP Clause

The SELECT TOP clause is used to specify the number of records to return.
The SELECT TOP clause is useful on large tables with thousands of records. Returning a large number of records can impact performance.





