# 🧥 Thrift & Handmade E-Commerce Database

## 📌 Overview
This project is a database design (ER model) for an e-commerce platform that sells thrifted and handmade products.

The system supports:
- customer management
- product catalog
- order processing
- inventory tracking
- payment handling
- shipment tracking

---

## 🧩 Database Schema

### 👤 customer
- customer_id (pk)
- customer_name
- customer_email (unique)
- customer_phone
- created_at
- updated_at

### 📍 address
- address_id (pk)
- customer_id (fk)
- address1, address2, landmark
- city, state
- created_at
- updated_at

### 📦 orders
- order_id (pk)
- customer_id (fk)
- order_date
- status
- total_amount
- discount_percentage
- created_at
- updated_at

### 🛒 order_item
- order_item_id (pk)
- order_id (fk)
- product_id (fk)
- quantity
- price_at_purchase
- created_at

### 🧥 product
- product_id (pk)
- name
- description
- price
- product_type (thrifted / handmade)
- category
- size
- color
- condition (new / used / vintage)
- is_unique
- created_at

### 📊 inventory
- inventory_id (pk)
- product_id (fk, unique)
- quantity_available
- created_at

### 💳 payment
- payment_id (pk)
- order_id (fk, unique)
- payment_date
- amount
- payment_method (upi / card / cod)
- payment_status (paid / pending / failed)

### 🚚 shipment
- shipment_id (pk)
- order_id (fk)
- address_id (fk)
- shipped_date
- delivery_date
- shipping_status (pending / shipped / delivered)

---

## 🔗 Relationships

customer.customer_id < address.customer_id  
customer.customer_id < orders.customer_id  

orders.order_id < order_item.order_id  
product.product_id < order_item.product_id  

product.product_id - inventory.product_id  

orders.order_id - payment.order_id  

orders.order_id < shipment.order_id  

address.address_id < shipment.address_id  

---

## 🎯 Key Features

- supports multiple orders per customer
- supports multiple products per order
- handles thrift (unique) and handmade (bulk) products
- maintains inventory separately
- tracks payments and shipment status
- normalized database structure

---

## 🧠 Design Highlights

- order_item resolves many-to-many relationship between orders and products  
- inventory supports both unique and bulk items  
- address is separated for flexibility  
- shipment supports multiple deliveries per order  

---

## 🏁 Conclusion

This database design is normalized, scalable, and suitable for real-world e-commerce systems.

---
## ER Diagram

The ER diagram is included in this repository as: 

<p align="center">
<img src="ER Diagram.png"n width="800">
</p>

