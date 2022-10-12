
**Schema (MySQL v8.0)**

    
    
    create table employee
    ( emp_ID int
    , emp_NAME varchar(50)
    , DEPT_NAME varchar(50)
    , SALARY int);
    
    insert into employee values(101, 'Mohan', 'Admin', 4000);
    insert into employee values(102, 'Rajkumar', 'HR', 3000);
    insert into employee values(103, 'Akbar', 'IT', 4000);
    insert into employee values(104, 'Dorvin', 'Finance', 6500);
    insert into employee values(105, 'Rohit', 'HR', 3000);
    insert into employee values(106, 'Rajesh',  'Finance', 5000);
    insert into employee values(107, 'Preet', 'HR', 7000);
    insert into employee values(108, 'Maryam', 'Admin', 4000);
    insert into employee values(109, 'Sanjay', 'IT', 6500);
    insert into employee values(110, 'Vasudha', 'IT', 7000);
    insert into employee values(111, 'Melinda', 'IT', 8000);
    insert into employee values(112, 'Komal', 'IT', 10000);
    insert into employee values(113, 'Gautham', 'Admin', 2000);
    insert into employee values(114, 'Manisha', 'HR', 3000);
    insert into employee values(115, 'Chandni', 'IT', 4500);
    insert into employee values(116, 'Satya', 'Finance', 6500);
    insert into employee values(117, 'Adarsh', 'HR', 3500);
    insert into employee values(118, 'Tejaswi', 'Finance', 5500);
    insert into employee values(119, 'Cory', 'HR', 8000);
    insert into employee values(120, 'Monica', 'Admin', 5000);
    insert into employee values(121, 'Rosalin', 'IT', 6000);
    insert into employee values(122, 'Ibrahim', 'IT', 8000);
    insert into employee values(123, 'Vikram', 'IT', 8000);
    insert into employee values(124, 'Dheeraj', 'IT', 11000);
    
    

---

**Query #1**

    select *, 
    row_number() over(partition by DEPT_NAME order by salary) as 'row_number()',
    dense_rank() over(partition by DEPT_NAME order by salary) as 'dense_rank()',
    rank() over(partition by DEPT_NAME order by salary) as 'rank()'
    
    from employee;

| emp_ID | emp_NAME | DEPT_NAME | SALARY | row_number() | dense_rank() | rank() |
| ------ | -------- | --------- | ------ | ------------ | ------------ | ------ |
| 113    | Gautham  | Admin     | 2000   | 1            | 1            | 1      |
| 101    | Mohan    | Admin     | 4000   | 2            | 2            | 2      |
| 108    | Maryam   | Admin     | 4000   | 3            | 2            | 2      |
| 120    | Monica   | Admin     | 5000   | 4            | 3            | 4      |
| 106    | Rajesh   | Finance   | 5000   | 1            | 1            | 1      |
| 118    | Tejaswi  | Finance   | 5500   | 2            | 2            | 2      |
| 104    | Dorvin   | Finance   | 6500   | 3            | 3            | 3      |
| 116    | Satya    | Finance   | 6500   | 4            | 3            | 3      |
| 102    | Rajkumar | HR        | 3000   | 1            | 1            | 1      |
| 114    | Manisha  | HR        | 3000   | 2            | 1            | 1      |
| 105    | Rohit    | HR        | 3000   | 3            | 1            | 1      |
| 117    | Adarsh   | HR        | 3500   | 4            | 2            | 4      |
| 107    | Preet    | HR        | 7000   | 5            | 3            | 5      |
| 119    | Cory     | HR        | 8000   | 6            | 4            | 6      |
| 103    | Akbar    | IT        | 4000   | 1            | 1            | 1      |
| 115    | Chandni  | IT        | 4500   | 2            | 2            | 2      |
| 121    | Rosalin  | IT        | 6000   | 3            | 3            | 3      |
| 109    | Sanjay   | IT        | 6500   | 4            | 4            | 4      |
| 110    | Vasudha  | IT        | 7000   | 5            | 5            | 5      |
| 111    | Melinda  | IT        | 8000   | 6            | 6            | 6      |
| 122    | Ibrahim  | IT        | 8000   | 7            | 6            | 6      |
| 123    | Vikram   | IT        | 8000   | 8            | 6            | 6      |
| 112    | Komal    | IT        | 10000  | 9            | 7            | 9      |
| 124    | Dheeraj  | IT        | 11000  | 10           | 8            | 10     |

---

[View on DB Fiddle](https://www.db-fiddle.com/)
