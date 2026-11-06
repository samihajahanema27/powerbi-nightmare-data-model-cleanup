# 📊 Power BI Data Modeling Project: Transforming a Nightmare Schema into a Clean Star Schema

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=power-bi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-Data%20Analysis%20Expressions-blue?style=for-the-badge)
![Data Modeling](https://img.shields.io/badge/Data%20Modeling-Star%20Schema-success?style=for-the-badge)

## 📌 Project Overview
This portfolio project demonstrates an end-to-end data modeling transformation in **Power BI**. Starting from a complex, inefficient "nightmare" data schema—characterized by bi-directional relationships, unnormalized tables, improper primary/foreign key mappings, and fact-to-fact connections—the project refactors the entire architecture into an optimized **Star Schema**.

Inspired by the end-to-end project framework by *Data with Baraa*, this project highlights the essential role of robust data modeling in ensuring accurate DAX measures, fast report performance, and scalable BI architecture.

---

## 🛠️ Key Challenges in the Initial Model ("Nightmare Model")
- **Bi-Directional Cross-Filtering Chaos:** Unintentional filter propagation creating ambiguous query paths and incorrect totals.
- **Fact-to-Fact Relationships:** Direct relationships between multiple event tables (e.g., `fact_sales` and `fact_inventory`).
- **Inconsistent Granularity:** Dimension tables with duplicate key values and mixed level-of-detail records.
- **Performance Bottlenecks:** Excess columns, redundant key columns, and unstandardized table schemas impacting memory usage.

---

## 💡 Key Transformations & Architecture Enhancements

### 1. Data Cleaning & Transformation (Power Query)
- **Granularity Definition:** Explicitly evaluated every table's grain to ensure one row represents a distinct, atomic entity.
- **Surrogate Keys:** Generated model-level surrogate keys with the `_key` suffix (e.g., `customer_key`, `product_key`) to separate business keys from data model relationships.
- **Data Reduction:** Dropped unnecessary audit/staging columns to minimize model size and boost in-memory performance.

### 2. Star Schema Implementation
- Built clear **Dimension Tables** (`dim_customers`, `dim_products`, `dim_locations`, `dim_date`, `dim_campaign`, etc.).
- Created centralized **Fact Tables** (`fact_sales`, `fact_order_process`, `fact_inventory`, `fact_campaign_spend`, etc.).
- Enforced single-direction (1-to-many) filter propagation flowing exclusively from **Dimensions -> Facts**.

### 3. Naming Conventions & Standards
- Applied standardized `snake_case` naming across all tables and fields.
- Applied explicit prefixes (`dim_` and `fact_`) for schema clarity.

---

## 📐 Data Model Comparison

| Initial State ("Nightmare Schema") | Refactored State ("Star Schema") |
| :--- | :--- |
| Untangled mesh of bi-directional filters | Clean 1-to-many single-direction filters |
| Direct Fact-to-Fact relationships | Shared dimension tables bridging fact tables |
| Ambiguous relationships causing inaccurate measure totals | Deterministic, highly performant measure calculations |

---

## 📊 Key Business Metrics (DAX Measures)
- **Total Sales:** `SUM(fact_sales[line_total])`
- **Total Orders:** `DISTINCTCOUNT(fact_sales[order_id])`
- **Total Active Customers:** Count of unique customers with purchases within selected timeframes.
- **Average Order to Pay:** Custom duration calculation tracking order fulfillment speed.

---

## 🚀 How to Run This Project
1. Clone this repository:
   ```bash
   git clone [https://github.com/YOUR_USERNAME/powerbi-nightmare-data-model-cleanup.git](https://github.com/YOUR_USERNAME/powerbi-nightmare-data-model-cleanup.git)
