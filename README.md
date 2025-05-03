# 🗃️ Stationery Store Management Database System

This project implements a comprehensive **Stationery Store Management Database System** using Oracle SQL. It covers essential entities and operations for managing a business’s customers, orders, products, suppliers, employees, and inventory movements, with built-in support for role-based access control, data integrity, and auditing.



## 📑 Table of Contents

* [Database Structure](#-database-structure)
* [Triggers and Sequences](#-triggers-and-sequences)
* [Roles and Permissions](#-roles-and-permissions)
* [Sample Data](#-sample-data)
* [Key Features](#-key-features)
* [How to Use](#-how-to-use)
* [Author](#-author)

---

## 🏗️ Database Structure

### 1. **Customer**

Stores customer information.

* `Customer_ID` (PK)
* `Name`
* `Phone`
* `Address`

### 2. **Order\_T**

Represents customer orders.

* `Order_ID` (PK)
* `Order_Date`
* `Customer_ID` (FK → Customer)

### 3. **Supplier**

Stores supplier details.

* `Supplier_ID` (PK)
* `Name`, `Phone`, `Email`, `Address`, `City`, `State`, `Postal_Code`

### 4. **Category**

Defines product categories.

* `Category_ID` (PK)
* `Name`

### 5. **Product**

Product inventory.

* `Product_ID` (PK)
* `Name`, `Unit_Price`, `Stock_Quantity`
* `Category_ID` (FK → Category)
* `Supplier_ID` (FK → Supplier)

### 6. **Order\_Item**

Mapping between orders and products.

* Composite PK: (`Order_ID`, `Product_ID`)
* `Quantity`

### 7. **Employee**

Employee details and payroll.

* `Employee_ID` (PK)
* `Name`, `Phone`, `Email`, `Address`, `City`, `Hire_Date`, `Salary`

### 8. **Inventory\_Transaction**

Tracks inventory movements.

* `Transaction_ID` (PK)
* `Quantity`, `Transaction_Date`, `Transaction_Type`
* `Employee_ID` (FK → Employee)
* `Product_ID` (FK → Product)

### 9. **Product\_Price\_Audit**

Audit table for price changes.

* `Audit_ID` (PK)
* `Product_ID` (FK)
* `Old_Price`, `New_Price`, `Change_Date`, `Changed_By`

---

## 🔁 Triggers and Sequences

* `update_product_stock`: Automatically reduces stock after a sale.
* `check_product_stock`: Prevents orders with insufficient inventory.
* `inv_trans_after_order`: Records sale in inventory log post-order.
* `audit_product_price_change`: Logs every product price update.
* `set_order_date`: Sets order date to system date if not provided.
* `SEQ_Transaction_ID`: Auto-increment sequence for inventory transactions.
* `Product_Price_Audit_Seq`: Sequence for audit IDs.

---

## 👥 Roles and Permissions

* **Admin**

  * Full access to create, modify, and manage all objects.
* **Manager**

  * Can read and update core business tables (Products, Orders, Inventory, Employees).
* **Salesperson**

  * Can create and manage customers and orders; limited product access.

---

## 📊 Sample Data

* **10 Customers** with names, phones, and addresses
* **10 Orders** linked to customers and specific dates
* **3 Suppliers** with full contact and address info
* *(Partial sample data shown; continue inserting as needed)*

---

## ✨ Key Features

* ✅ **Data Integrity**: Enforced through primary/foreign keys and constraints
* 🔄 **Automatic Stock Management**: Stock adjusted with order placements
* 🧾 **Price Change Auditing**: Tracks all unit price changes in a dedicated audit table
* 👥 **Role-Based Access Control**: Admin, Manager, and Salesperson privileges
* 🔄 **Triggers for Automation**: Seamless data consistency and automation for critical events

---

## 🚀 How to Use

1. Connect to your Oracle DB environment.
2. Execute the full SQL script (preferably in a tool like SQL Developer or Oracle APEX).
3. Review and manage the data through CRUD operations.
4. Test roles by creating users and granting appropriate roles.
5. Extend the system as needed (e.g., add views, stored procedures, or reporting).

---

## 👨‍💻 Author

**Subhan Amjad**
📧 [subhanamjad507@gmail.com](mailto:subhanamjad507@gmail.com)
🔗 [Linktree](https://linktr.ee/subhanamjad)
🎓 Student @ PIEAS | AI & DB Systems Enthusiast

---

Let me know if you’d like this in downloadable `.md` format or extended to include more dummy data or ERD diagrams!
