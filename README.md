# Project Title

**Employee Database — Querying Data (MySQL Assignment 2)**

---

## Problem Statement

Continuing from Assignment 1's constrained Employee Database, this project populates the `Departments`, `Location`, and `Employees` tables with real data and then queries that data to answer common business questions — filtering, sorting, aggregating, grouping, and joining across the three tables.

---

## Database Details

Built on the schema from Assignment 1 (`employee` database):

| Table | Row Count | Notes |
|---|---|---|
| **departments** | 13 | department_id (PK), department_name |
| **location** | 4 | location_id (PK, auto-increment), location_name — Chennai, Bangalore, Hyderabad, Pune |
| **employees** | 30 | employee_id (PK), employee_name, gender, age, hire_date, designation, salary, department_id (FK), location_id (FK) |

One employee (Kiara Malhotra, ID 5004) was inserted with a `NULL` designation and later updated to `'Data Scientist'` as part of Task 3.

---

## List of SQL Concepts Used

- `DISTINCT`
- Column aliasing (`AS`)
- `WHERE` with comparison and logical operators, `IS NULL`
- `UPDATE`
- `ORDER BY` (multi-column, mixed `ASC`/`DESC`)
- `LIMIT`
- Aggregate functions — `SUM`, `MIN`, `MAX`, `AVG`
- `GROUP BY`
- `HAVING`
- `INNER JOIN`, `LEFT JOIN`, `RIGHT JOIN`

---

## Query Explanations

1. **Distinct Values** — `SELECT DISTINCT salary` returns each unique salary value, removing duplicates.
2. **Alias** — `age AS Employee_Age, salary AS Employee_Salary` relabels columns in the result set for readability.
3. **Where Clause & Operators** — filters employees earning above ₹50,000 and hired before 2016-01-01; a separate query finds the employee with a missing designation, then an `UPDATE` fills it in with `'Data Scientist'`.
4. **Order By** — sorts employees by `department_id` ascending, then `salary` descending within each department.
5. **Limit** — filters employees hired in 2018, orders by hire date, and returns only the first 5.
6. **Aggregate Functions** — `SUM(salary)` joined against `departments` totals pay in the Finance department; `MIN(age)` finds the youngest employee company-wide.
7. **Group By** — `MAX(salary)` grouped by location finds the top earner's salary per city; `AVG(salary)` grouped by designation (filtered to titles containing "Analyst") compares pay across analyst roles.
8. **Having** — a `LEFT JOIN` + `GROUP BY` + `HAVING COUNT(...) < 3` finds understaffed departments (including any with zero employees); a similar pattern filters to locations where the average age of female employees is under 30.
9. **Inner Join** — combines `employees` and `departments` to list each employee's name, designation, and department, excluding any unmatched rows.
10. **Left Join** — counts employees per department, keeping departments with zero employees in the result (`COUNT` returns 0 for those).
11. **Right Join** — lists employees per location, keeping locations with no assigned employees (employee name shows as `NULL` for those).

---

## Conclusion

This assignment exercises the core SQL querying toolkit — filtering, sorting, aliasing, aggregation, grouping with conditions, and all three major join types — against a realistic 30-row employee dataset spanning 13 departments and 4 locations. Together with Assignment 1's schema and constraints work, it demonstrates the ability to both design a relational database and extract meaningful insights from it, a core skill for a Data Analyst role.

**Files in this repository:**
- `Ass2.sql` — all Assignment 2 queries (Tasks 1–11), to be run after the data is loaded
- `employee data.sql` — INSERT statements populating Departments, Location, and Employees
- `Report.pdf` — one-page summary of what was completed
