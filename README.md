# Ex. No: 6 Creating Cursors using PL/SQL

## DATE:26/09/2023

### AIM: 

To create a cursor using PL/SQL.

### Steps:
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create a cursor named as employee_cursor
3. Using cursor read each record and display the result
4. Close the cursor

### Program:
### Create employee table
```sql
CREATE TABLE employeee(empid NUMBER,empname VARCHAR2(10),dept VARCHAR2(10),salary NUMBER);
INSERT INTO employeee (empid, empname, dept, salary) VALUES (1, 'John', 'HR', 50000);
INSERT INTO employeee (empid, empname, dept, salary) VALUES (2, 'Joe', 'IT', 65000);
INSERT INTO employeee (empid, empname, dept, salary) VALUES (3, 'Bob', 'Finance', 55000);
```

### PLSQL Cursor code
```sql
SET SERVEROUTPUT ON
DECLARE
    CURSOR employee_cursor IS
        SELECT empid, empname, dept, salary
        FROM employee;
    empid NUMBER;
    empname VARCHAR2(90);
    dept VARCHAR2(90);
    salary NUMBER;
BEGIN
    OPEN employee_cursor;
    LOOP
        FETCH employee_cursor INTO empid, empname, dept, salary;
        EXIT WHEN employee_cursor%NOTFOUND;
        DBMS_OUTPUT.PUT_LINE('Employee ID: ' || empid);
        DBMS_OUTPUT.PUT_LINE('Employee Name: ' || empname);
        DBMS_OUTPUT.PUT_LINE('Department: ' || dept);
        DBMS_OUTPUT.PUT_LINE('Salary: ' || salary);
        DBMS_OUTPUT.PUT_LINE('------------------------');
    END LOOP;
    CLOSE employee_cursor;
END;
/
```
### Output:
![Screenshot 2023-10-03 161505](https://github.com/Adhithyaram29D/Ex-no-6-Creating-Cursors-using-PL-SQL/assets/119393540/4ffcc3b8-8991-4c79-a5c4-9d498a1e69f7)

### Result:
Hence a cursor using PL/SQL is created successfully.
