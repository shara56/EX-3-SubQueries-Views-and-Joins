# EX-3-SubQueries-Views-and-Joins
## Create employee Table
```
CREATE TABLE EMP (EMPNO NUMBER(4) PRIMARY KEY,ENAME VARCHAR2(10),JOB VARCHAR2(9),MGR NUMBER(4),HIREDATE DATE,SAL NUMBER(7,2),COMM NUMBER(7,2),DEPTNO NUMBER(2));
```
## Insert the values
```
INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7369, 'SMITH', 'CLERK', 7902, '17-DEC-80', 800, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7499, 'ALLEN', 'SALESMAN', 7698, '20-FEB-81', 1600, 300, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7521, 'WARD', 'SALESMAN', 7698, '22-FEB-81', 1250, 500, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7566, 'JONES', 'MANAGER', 7839, '02-APR-81', 2975, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7654, 'MARTIN', 'SALESMAN', 7698, '28-SEP-81', 1250, 1400, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7698, 'BLAKE', 'MANAGER', 7839, '01-MAY-81', 2850, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7782, 'CLARK', 'MANAGER', 7839, '09-JUN-81', 2450, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7788, 'SCOTT', 'ANALYST', 7566, '19-APR-87', 3000, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7839, 'KING', 'PRESIDENT', NULL, '17-NOV-81', 5000, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7844, 'TURNER', 'SALESMAN', 7698, '08-SEP-81', 1500, 0, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7876, 'ADAMS', 'CLERK', 7788, '23-MAY-87', 1100, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7900, 'JAMES', 'CLERK', 7698, '03-DEC-81', 950, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7902, 'FORD', 'ANALYST', 7566, TO_DATE('03-DEC-81', 'DD-MON-RR'), 3000, 20, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7934, 'MILLER', 'CLERK', 7782, TO_DATE('23-JAN-82', 'DD-MON-RR'), 1300, 10, 10);
```
## Create department table
```
CREATE TABLE DEPT (DEPTNO NUMBER(2) PRIMARY KEY,DNAME VARCHAR2(14),LOC VARCHAR2(13));
```
## Insert the values in the department table
```
INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (10, 'ACCOUNTING', 'NEW YORK');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (20, 'RESEARCH', 'DALLAS');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (30, 'SALES', 'CHICAGO');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (40, 'OPERATIONS', 'BOSTON');
```
## Q1) List the name of the employees whose salary is greater than that of employee with empno 7566.
## QUERY:
```
CREATE VIEW details AS SELECT ENAME FROM EMP WHERE SAL >(select SAL from EMP where EMPNO=7566);
```
## OUTPUT:
![image](https://github.com/shara56/EX-3-SubQueries-Views-and-Joins/assets/113497104/1d807d9d-57b0-433c-b263-0c8b570b90ef)
## Q2) List the ename,job,sal of the employee who get minimum salary in the company.
## QUERY:
```
CREATE VIEW minimum AS select ENAME,JOB,SAL from EMP where SAL =(select MIN(SAL) from EMP);
```
## OUTPUT:
![image](https://github.com/shara56/EX-3-SubQueries-Views-and-Joins/assets/113497104/4c7ed62c-52ef-4fbf-914c-2cf33fb21a27)
## Q3) List ename, job of the employees who work in deptno 10 and his/her job is any one of the job in the department ‘SALES’.
## QUERY:
```
select ENAME,JOB from EMP where  DEPTNO=10 AND JOB='SALESMAN';
```
## OUTPUT:
![image](https://github.com/shara56/EX-3-SubQueries-Views-and-Joins/assets/113497104/fe321028-c78c-45bf-a02a-31f950fdf105)
## Q4) Create a view empv5 (for the table emp) that contains empno, ename, job of the employees who work in dept 10.
## QUERY:
```
create view empv5 as select EMPNO,ENAME,JOB from EMP where DEPTNO=10;
```
## OUTPUT:
![image](https://github.com/shara56/EX-3-SubQueries-Views-and-Joins/assets/113497104/e63e908c-f45a-4c58-a9f9-a6f31083ea49)
## Q5) Create a view with column aliases empv30 that contains empno, ename, sal of the employees who work in dept 30. Also display the contents of the view.
## QUERY:
```
create view empv30 AS select EMPNO,ENAME,SAL from EMP where DEPTNO=30;
```
## OUTPUT:
![image](https://github.com/shara56/EX-3-SubQueries-Views-and-Joins/assets/113497104/03d718f8-997f-4f59-ad08-b0d3f98dc569)
## Q6) Update the view empv5 by increasing 10% salary of the employees who work as ‘CLERK’. Also confirm the modifications in emp table
## QUERY:
```
update EMP set SAL=SAL*1.1 WHERE JOB='clerk';

create view empv8 as select EMPNO,ENAME,SAL,JOB from EMP;
```
## OUTPUT:
![image](https://github.com/shara56/EX-3-SubQueries-Views-and-Joins/assets/113497104/ac7c7a5f-8afb-4b76-abb8-43040bb10122)
## Create a Customer1 Table
```
CREATE TABLE Customer1 (customer_id INT,cust_name VARCHAR(20),city VARCHAR(20),grade INT,salesman_id INT);
```
## Inserting Values to the Table
```
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3002, 'Nick Rimando', 'New York', 100, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3007, 'Brad Davis', 'New York', 200, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3005, 'Graham Zusi', 'California', 200, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3008, 'Julian Green', 'London', 300, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3004, 'Fabian Johnson', 'Paris', 300, 5006);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3009, 'Geoff Cameron', 'Berlin', 100, 5003);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3003, 'Jozy Altidor', 'Moscow', 200, 5007);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3001, 'Brad Guzan', 'London', NULL, 5005);
```
## Create a Salesperson1 table
```
CREATE TABLE Salesman1 (salesman_id INT,name VARCHAR(20),city VARCHAR(20),commission DECIMAL(4,2));
```
## Inserting Values to the Table
```
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5001, 'James Hoog', 'New York', 0.15);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5002, 'Nail Knite', 'Paris', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5005, 'Pit Alex', 'London', 0.11);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5006, 'Mc Lyon', 'Paris', 0.14);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5007, 'Paul Adam', 'Rome', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5003, 'Lauson Hen', 'San Jose', 0.12);
```
## Q7) Write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.
## QUERY:
```
SELECT salesman1.name AS "Salesman", customer1.cust_name AS "Customer Name", salesman1.city AS "City" from salesman1 INNER JOIN customer1 ON salesman1.city=customer1.city;
```
## OUTPUT:
![image](https://github.com/shara56/EX-3-SubQueries-Views-and-Joins/assets/113497104/2265d6f2-5c23-4265-95fb-1912fefa3521)
## Q8) Write a SQL query to find salespeople who received commissions of more than 13 percent from the company. Return Customer Name, customer city, Salesman, commission.
## QUERY:
```
SELECT customer1.cust_name AS "Customer Name",customer1.city AS "Customer City",salesman1.name AS "Salesman",salesman1.commission AS "Commission" FROM salesman1 INNER JOIN customer1 ON salesman1.salesman_id=customer1.salesman_id WHERE salesman1.commission>0.13;
```
## OUTPUT:
![image](https://github.com/shara56/EX-3-SubQueries-Views-and-Joins/assets/113497104/d652d0d5-4b71-4bc0-a2c9-325f112675dc)
## Q9) Perform Natural join on both tables
## QUERY:
```
SELECT customer1.cust_name AS "Customer Name",customer1.city AS "Customer City",salesman1.name AS "Salesman",salesman1.commission AS "Commission" FROM salesman1 INNER JOIN customer1 ON salesman1.salesman_id=customer1.salesman_id WHERE salesman1.commission>0.13;
```
## OUTPUT:
![image](https://github.com/shara56/EX-3-SubQueries-Views-and-Joins/assets/113497104/840c7f44-b6a3-4d27-b0f7-7d390bf3ce87)
## Q10) Perform Left and right join on both tables
## QUERY FOR LEFT JOIN:
```
SELECT customer1.cust_name AS "Customer Name",customer1.city AS "Customer City",salesman1.name AS "Salesman",salesman1.commissioSELECT customer1.cust_name AS "Customer Name",customer1.city AS "Customer City",salesman1.name AS "Salesman",salesman1.commission AS "Commission" FROM salesman1 INNER JOIN customer1 ON salesman1.salesman_id=customer1.salesman_id WHERE salesman1.commission>0.13;
```
```
select * from customer1 natural join salesman1;
```
## OUTPUT FOR LEFT JOIN:
![image](https://github.com/shara56/EX-3-SubQueries-Views-and-Joins/assets/113497104/5c848bd9-f4b5-4e08-a839-698402aea308)
## QUERY FOR RIGHT JOIN:
```
SELECT * FROM salesman1 RIGHT JOIN customer1 ON salesman1.salesman_id=customer1.salesman_id;
```
## OUTPUT FOR RIGHT JOIN:
![image](https://github.com/shara56/EX-3-SubQueries-Views-and-Joins/assets/113497104/e057992b-0935-4f4f-ac19-268650fb372e)
