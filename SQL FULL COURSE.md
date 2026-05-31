------- SQL introduction------
- Is a programing language used to intereact with database
- data stored in tables in sql format like rows,coulmns,etc


 ----operations(CURD)----
    C -CREATE
    U- UPDATE
    R- READ
    D- DELETE
    
    

    
The main SQL data types:

🔢 1. Numeric Data Types
Used for numbers.

INT / INTEGER → whole numbers
Example: 10, -5, 1000

SMALLINT → smaller range integers

BIGINT → very large integers

DECIMAL(p,s) / NUMERIC(p,s) → exact numbers (used for money)
Example: DECIMAL(10,2) → 12345.67

FLOAT / REAL / DOUBLE → approximate decimal numbers
Example: 3.14, 0.001

🧾 2. Character / String Data Types
Used for text.

CHAR(n) → fixed-length string
Example: CHAR(5) → "Hi "

VARCHAR(n) → variable-length string
Example: "Hello"

TEXT → large text data (paragraphs, descriptions)

📅 3. Date and Time Data Types
Used for storing dates and times.

DATE → only date
Example: 2026-05-31

TIME → only time
Example: 14:30:00

DATETIME / TIMESTAMP → date + time
Example: 2026-05-31 14:30:00

✅ 4. Boolean Type
BOOLEAN / BOOL → true or false
Example: TRUE, FALSE

📦 5. Binary Data Types
Used for images, files, etc.

BLOB → Binary Large Object

BINARY / VARBINARY → store binary data

🧩 Example Table
CREATE TABLE Students (
    id INT,
    name VARCHAR(50),
    age INT,
    marks DECIMAL(5,2),
    dob DATE,
    is_active BOOLEAN
);




---- The main SQL constraints with clear examples:------

1. NOT NULL Constraint: 
 Prevents a column from having NULL values.

Example:
CREATE TABLE Students (
    ID INT NOT NULL,
    Name VARCHAR(50) NOT NULL
);
👉 Meaning: Every student must have an ID and Name.

2. UNIQUE Constraint:
  Ensures all values in a column are different.

Example:
CREATE TABLE Users (
    UserID INT UNIQUE,
    Email VARCHAR(100) UNIQUE
);
👉 Meaning: No two users can have the same email.

3. PRIMARY KEY Constraint:
  Uniquely identifies each record in a table (NOT NULL + UNIQUE).
Example:
CREATE TABLE Employees (
    EmpID INT PRIMARY KEY,
    Name VARCHAR(50)
);
👉 Meaning: Each employee has a unique EmpID.

4. FOREIGN KEY Constraint:
 Links one table to another (maintains referential integrity).

Example:
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    EmpID INT,
    FOREIGN KEY (EmpID) REFERENCES Employees(EmpID)
);
👉 Meaning: Every order must belong to a valid employee.

5. CHECK Constraint:
 Ensures values meet a condition.

Example:
CREATE TABLE Products (
    ProductID INT PRIMARY KEY,
    Price DECIMAL(10,2),
    CHECK (Price > 0)
);
👉 Meaning: Price must always be greater than 0.

6. DEFAULT Constraint:
 Provides a default value if none is given.

Example:
CREATE TABLE Accounts (
    AccountID INT PRIMARY KEY,
    Status VARCHAR(20) DEFAULT 'Active'
);
👉 Meaning: If no status is given, it becomes "Active".

7. AUTO INCREMENT: 
 used to automatically generate a unique number for a column (usually the primary key) every time a new row is inserted

Example:
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100)
);

# Quick Summary

----Constraint Purpose--

NOT NULL: No empty values allowed
UNIQUE:	No duplicate values
PRIMARY KEY: Unique row identifier
FOREIGN KEY:	Links tables
CHECK:	Validates condition
DEFAULT: Sets default value

# SQL COMMANDS ------


    ------SQL COMMANDS(5TYPES)-----
    1) DDL- DATA DEFINITION LANGUAGE
    SYNTAX: CREATE, ALTER ,DROP, TRUNCATE, RENAME
    (used to define database structures)
    
    2) DML: DATA MANIPULATION LANGUAGE
    SYNATX:  INSERT, UPDATE,DELETE
    (used to manipulate data in database)

    3)DCL: DATA CONTROL LANGUAGE
    SYNTAX: GRANT, REVOKE
    (used for acces control in database)

    4) DQL: DATA QUERY LANGUAGE
    SYNTAX: SLECT
    ( used to retrive data form database)

    5) TCL: TRANSACTION CONTROL LANGUAGE
    SYNTAX: COMMIT, ROLLBACK, SAVEPOINT
    (used to manage transcations)




------------- SQL COMMANDS AND SYNTAX'S -----------------


🔹 DDL (Data Definition Language):
Used to define or modify database structure

Create table: "For createing a table"

synatx:

CREATE TABLE table_name (
    column1 datatype,
    column2 datatype
);

Alter table: "For add column to table"

synatx:

ALTER TABLE table_name
ADD column_name datatype;

Drop table: "to delete entire table"

synatx:

DROP TABLE table_name;

Truncate table: "To delete data inside the table"

 synatx:

TRUNCATE TABLE table_name;


🔹 DML (Data Manipulation Language):
Used to manage data inside tables

Insert table: "for inserting data into table"

syntax:

INSERT INTO table_name (column1, column2)
VALUES (value1, value2);

Update table: " To update the table "

syntax:

UPDATE table_name
SET column1 = value1
WHERE condition;
Delete table: " T delete table "

syntax:

DELETE FROM table_name
WHERE condition;


🔹 DQL (Data Query Language):
Used to retrieve data
select table: " To read or retrive data form table"

synatx:

SELECT column1, column2
FROM table_name
WHERE condition;


🔹 DCL (Data Control Language):
Used for permissions and access control

GRANT : "TO access permission or grant permission"

synatx:

GRANT privilege_name
ON object_name
TO user_name;

Revoke : "to declined or remove permisssion"

syntax:

REVOKE privilege_name
ON object_name
FROM user_name;


🔹 TCL (Transaction Control Language):
Used to manage transactions

Commit : " To save permatntly"

syntax:
COMMIT;

Rollback: " to rollback to pervious step or to undo your step"

syntax:
ROLLBACK;

Savepoint: " To save a point in your program"

syntax:
SAVEPOINT savepoint_name;





-------- The main SQL operators --------

1. Arithmetic Operators:
Used for mathematical calculations.

Operator	                 MeaningExample
+	Addition	             SELECT 10 + 5; → 15
-	Subtraction              SELECT 10 - 5; → 5
*	Multiplication           SELECT 10 * 5; → 50
/	Division	             SELECT 10 / 5; → 2
%	Modulus (remainder)	     SELECT 10 % 3; → 1
 
 Example with table:

SELECT salary, salary + 1000 AS new_salary
FROM employees;

2. Comparison Operators:
Used in WHERE conditions.

Operato           	Meaning	Example
=	Equal to	    salary = 50000
!= or <> Not equal	salary <> 50000
>	Greater than	salary > 50000
<	Less than       salary < 50000
>= Greater or equal	salary >= 50000
<=	Less or equal	salary <= 50000

Example:

SELECT * 
FROM employees
WHERE salary > 50000;

3. Logical Operators:
Used to combine multiple conditions.

Operator	Meaning
AND	        All conditions must be true
OR	        Any condition can be true
NOT	        Reverses condition

Examples:

SELECT * 
FROM employees
WHERE salary > 50000 AND department = 'IT';
SELECT * 
FROM employees
WHERE department = 'IT' OR department = 'HR';
SELECT * 
FROM employees
WHERE NOT department = 'HR';

4. Special Operators:

a) BETWEEN:
Checks range (inclusive).

Example:

SELECT * 
FROM employees
WHERE salary BETWEEN 30000 AND 60000;

b) IN:
Matches multiple values.

Example:

SELECT * 
FROM employees
WHERE department IN ('IT', 'HR', 'Finance');

c) LIKE:
Pattern matching.

Symbol	Meaning
%	    Any sequence
_	    Single character

Examples:

SELECT * 
FROM employees
WHERE name LIKE 'A%';   -- starts with A
SELECT * 
FROM employees
WHERE name LIKE '_a%';  -- second letter is a


d) IS NULL:
Checks NULL values.

Example:

SELECT * 
FROM employees
WHERE manager_id IS NULL;

e) EXISTS:
Checks if subquery returns rows.

Example:

SELECT * 
FROM departments d
WHERE EXISTS (
    SELECT 1 
    FROM employees e
    WHERE e.department_id = d.id
);
f) ANY / ALL:
Used with subqueries.

ANY example:

SELECT * 
FROM employees
WHERE salary > ANY (
    SELECT salary FROM employees WHERE department = 'IT'
);
ALL example:

SELECT * 
FROM employees
WHERE salary > ALL (
    SELECT salary FROM employees WHERE department = 'HR'
);

5. Bitwise Operators (DB-dependent, mostly MySQL)
Operator	Meaning
&	       Bitwise AND
|	       Bitwise OR
^	       Bitwise XOR
<<	       Left shift
>>	      Right shift

Example:

SELECT 5 & 3;  -- output: 1

# Quick Summary

Arithmetic → calculations

Comparison → filtering values

Logical → combine conditions

Special → advanced filtering (IN, LIKE, BETWEEN, NULL, subqueries)

Bitwise → binary operations





------  THE MAIN SQL AGGRAETE FUNCTIONS WITH SYNTAX AND EXAMPLES: -------

1. COUNT():
Counts number of rows

Syntax:
SELECT COUNT(column_name)
FROM table_name;

Example:
SELECT COUNT(*) AS total_employees
FROM employees;

2. SUM():
Adds values of a numeric column

Syntax:
SELECT SUM(column_name)
FROM table_name;

Example:
SELECT SUM(salary) AS total_salary
FROM employees;

3. AVG():
Finds average value

Syntax:
SELECT AVG(column_name)
FROM table_name;

Example:
SELECT AVG(salary) AS average_salary
FROM employees;

4. MIN():
Finds smallest value

Syntax:
SELECT MIN(column_name)
FROM table_name;

Example:
SELECT MIN(salary) AS lowest_salary
FROM employees;

5. MAX():
Finds largest value

Syntax:
SELECT MAX(column_name)
FROM table_name;

Example:
SELECT MAX(salary) AS highest_salary
FROM employees;


 ---------------GROUPBY & HAVING FUNCTIONS WITH AGGREATE FUNCTIONS-----------------

#  GROUPBY FUNCTION WITH AGGREATE FUNCTIONS:

6. GROUP BY (used with aggregates):
Used to group rows before applying aggregate functions

Syntax:
SELECT column_name, AGGREGATE_FUNCTION(column_name)
FROM table_name
GROUP BY column_name;

Example:
SELECT department, AVG(salary)
FROM employees
GROUP BY department;
# HAVING FUNCTION WITH AGGRETATE FUNCTIONS:

7. HAVING (filter after aggregation):
Like WHERE but used for grouped results

Syntax:
SELECT column_name, COUNT(*)
FROM table_name
GROUP BY column_name
HAVING condition;

Example:
SELECT department, COUNT(*) AS total
FROM employees
GROUP BY department
HAVING COUNT(*) > 5;






------- #JOINS///////// -------

JOIN:
In SQL, JOINs are used to combine rows from two or more tables based on a related column.

TYPES OF JOINS WITH SYNTAX AND EXAMPLES:

1. INNER JOIN:

Returns only matching rows from both tables.

Syntax:

SELECT columns
FROM table1
INNER JOIN table2
ON table1.common_column = table2.common_column;

Example:
Employees( table_name)

id	name
1	Ravi
2	srinu

Departments(table_name)

emp_id	dept
1	IT
2	HR

Query:

SELECT Employees.name, Departments.dept
FROM Employees
INNER JOIN Departments
ON Employees.id = Departments.emp_id;


2. LEFT JOIN (LEFT OUTER JOIN):

Returns all rows from left table + matching rows from right table.

Syntax:

SELECT columns
FROM table1
LEFT JOIN table2
ON table1.common_column = table2.common_column;

Example:
SELECT Employees.name, Departments.dept
FROM Employees
LEFT JOIN Departments
ON Employees.id = Departments.emp_id;

👉 If an employee has no department, dept will be NULL.

3. RIGHT JOIN (RIGHT OUTER JOIN):

Returns all rows from right table + matching rows from left table.

Syntax:
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.common_column = table2.common_column;

Example:
SELECT Employees.name, Departments.dept
FROM Employees
RIGHT JOIN Departments
ON Employees.id = Departments.emp_id;

4. FULL OUTER JOIN:

Returns all rows when there is a match in either table.

Syntax:

SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.common_column = table2.common_column;

Example:

SELECT Employees.name, Departments.dept
FROM Employees
FULL OUTER JOIN Departments
ON Employees.id = Departments.emp_id;

👉 Includes:
matched rows
unmatched rows from both tables

5. CROSS JOIN:

Returns Cartesian product (all combinations).

Syntax:

SELECT columns
FROM table1
CROSS JOIN table2;

Example:

SELECT Employees.name, Departments.dept
FROM Employees
CROSS JOIN Departments;

👉 If 2 employees and 3 departments → 6 rows.

6. SELF JOIN:

A table joined with itself.

Syntax:

SELECT a.column, b.column
FROM table_name a
JOIN table_name b
ON a.common_column = b.common_column;

Example:
(Employee hierarchy)

SELECT E1.name AS Employee, E2.name AS Manager
FROM Employees E1
JOIN Employees E2
ON E1.manager_id = E2.id;

 # Quick Summary Table    ///////------------

JOIN Type	       Result
INNER JOIN     	   Matching rows only
LEFT JOIN	       All left + matched right
RIGHT JOIN	       All right + matched left
FULL JOIN	       All rows from both
CROSS JOIN	       All combinations
SELF JOIN	       Table joins itself


 ////////////  BASIC SQL COMMANDS ///////////////

 TO CREATE DATABASE:
              SYNTAX : CREATE DATABASE database_name;

   
 TO USE DATABASE :
            SYNTAX: USE database_name;
            
            

TO SHOW DATABASES:
          SYNTAX: SHOW DATABASES;
           



-------------- SQL  WRTIEING CODE ORDER AND EXCUTEION ORDER  --------------------



Here is a clear table showing both:

//////////   SQL Query Writing Order vs Execution Order  //////////

Step	    Writing Order (Syntax)	      Execution Order (Logical)	                  What happens
1	            SELECT	                              5	                          Final output columns are chosen
2               FROM	                              1	                          Tables are loaded
3	            JOIN	                              2	                          Tables are joined
4	            WHERE	                              3	                          Rows are filtered
5	           GROUP BY	                              4	                          Rows are grouped
6	            HAVING	                              6                           Groups are filtered
7	         SELECT DISTINCT	                      7	                          Duplicates removed (if used)
8	            ORDER BY	                          8	                          Results are sorted
9 	         LIMIT / OFFSET	                          9	                         Final rows are restricted


Example SQL Query: "Writing order "

SELECT department, COUNT(*) 
FROM employees
WHERE salary > 30000
GROUP BY department
HAVING COUNT(*) > 2
ORDER BY COUNT(*) DESC
LIMIT 5;


Execution  order:

FROM employees

WHERE salary > 30000

GROUP BY department

HAVING COUNT(*) > 2

SELECT department, COUNT(*)

ORDER BY COUNT(*) DESC

LIMIT 5
































