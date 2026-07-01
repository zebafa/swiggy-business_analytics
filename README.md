# Swiggy Business Analytics — Databricks SQL Data Warehouse

An end-to-end business analytics project built on a star-schema data warehouse in **Databricks SQL**, analyzing 100,000+ Swiggy food-delivery transactions to surface insights on revenue, customer retention, delivery performance, coupon/campaign ROI, and operational data quality.

## Overview

This project simulates a real-world analytics engineering + BI workflow: rather than working off a single flat CSV, the data is modeled as a proper **fact and dimension schema**, then queried with production-style SQL (CTEs, window functions, multi-table joins) to answer the kinds of questions a food-delivery business analyst would actually be asked.

## Data Model

**Fact table**
- `swiggy_fact_transactions` — one row per order, including transaction date/time, city, device type, gross/net amount, coupon and discount details, delivery time, delivery success flag, campaign exposure/click flags, and customer rating/feedback.

**Dimension tables**
- `dim_customer` — customer demographics: name, gender, age, signup date, membership tier
- `dim_geo` — city, state, pincode
- `dim_restaurant_product` — restaurant name, product name, cuisine tag, list price
- `dim_coupon` — coupon name, discount type/value, max discount, minimum order value

This star-schema design supports fast aggregation across business dimensions (city, time, customer segment, product, campaign) without repeatedly scanning raw transaction-level data.

## Key Analyses

**Revenue & Growth**
- Monthly net revenue by city
- Monthly coupon discount burn as a % of gross revenue
- Membership benefit share of total discounts

**Customer Insights**
- Top spenders in the last 30 days
- Monthly repeat-order rate (cohort-style retention analysis)
- Demographic segmentation by age band, gender, and membership tier

**Delivery Operations**
- Average delivery time by city
- Delivery success rate by city and device type
- Rain vs. normal-weather delivery time impact
- Worst 5% of deliveries (P95 delivery time + failed deliveries) for SLA investigation

**Marketing & Coupons**
- Coupon usage rate and total discount burn
- Coupon performance by coupon type (orders driven, average order value with/without coupon)
- Campaign click-through rate (CTR)
- Exposed vs. non-exposed average order value (campaign lift analysis)

**Product & Pricing**
- Top 5 cuisines per city per month
- Restaurant leaderboard (orders and revenue, last 60 days)
- Product basket analysis (quantity and revenue by product/city)
- Price realization check (list price vs. actual realized price per unit)

**Data Quality**
- Orphan-record checks between fact and dimension tables to validate referential integrity before reporting

## Tech Stack

- **Databricks SQL** — data modeling and query execution
- **SQL** — CTEs, window functions, multi-table joins, conditional aggregation
- **Power BI** — dashboarding and stakeholder-facing visualization

## Skills Demonstrated

- Dimensional (star-schema) data modeling
- Advanced SQL for business analytics (cohort analysis, percentile calculations, conditional aggregation)
- Data quality validation
- Translating business questions (retention, campaign ROI, delivery SLAs) into query logic
- BI dashboard reporting for stakeholders

## Sample Business Questions Answered

- Which cities generate the most revenue, and how is that trending month over month?
- What % of orders use coupons, and how much margin do coupons cost the business?
- Are marketing campaigns actually increasing average order value?
- Which cities/devices have the worst delivery reliability, and does weather make it worse?
- Which customers are most valuable, and how many customers are repeat buyers each month?

---

*Note: This project uses a synthetic/sample Swiggy-style transactions dataset for learning and portfolio purposes.*
