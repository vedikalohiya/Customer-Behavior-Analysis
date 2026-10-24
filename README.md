# Customer Shopping Behavior Analysis

End-to-end analysis of 3,900 retail purchases to understand what drives customer spending, loyalty and subscriptions. The project covers data preparation in **Python**, business analysis in **PostgreSQL**, an interactive **Power BI** dashboard, and a report and presentation with recommendations.

---

## Business Problem

A retail company has seen shifting purchase patterns across demographics, product categories and sales channels. Management wants to know which factors (discounts, reviews, seasons, payment preferences, shipping) drive purchases and repeat buying.

> **How can the company leverage consumer shopping data to identify trends, improve customer engagement, and optimize marketing and product strategies?**

Full brief: [Business Problem Document.pdf](Business%20Problem%20%20Document.pdf)

---

## Dataset

| Item | Detail |
|---|---|
| File | `customer_shopping_behavior.csv` |
| Rows / Columns | 3,900 / 18 |
| Demographics | Age, Gender, Location, Subscription Status |
| Purchase details | Item Purchased, Category, Purchase Amount (USD), Season, Size, Color |
| Behavior | Discount Applied, Promo Code Used, Previous Purchases, Payment Method, Frequency of Purchases, Review Rating, Shipping Type |
| Data quality | 37 missing values in `Review Rating` |

---

## Workflow

### 1. Data preparation (Python)
- Loaded the data with `pandas` and profiled it using `df.info()` and `.describe()`.
- Imputed the 37 missing `Review Rating` values using the **median rating of each product category**.
- Renamed columns to **snake_case**.
- Engineered `age_group` (binned ages) and `purchase_frequency_days`.
- Found `promo_code_used` redundant with `discount_applied` and dropped it.
- Loaded the cleaned DataFrame into **PostgreSQL**.

### 2. Analysis (PostgreSQL)
Ten business questions answered in [`pg sql.sql`](pg%20sql.sql):

1. Revenue by gender
2. High-spending customers who used discounts (839 customers)
3. Top 5 products by average rating
4. Standard vs. Express shipping: average purchase amount
5. Subscribers vs. non-subscribers
6. Most discount-dependent products
7. Customer segmentation (New / Returning / Loyal)
8. Top 3 products per category
9. Repeat buyers (>5 purchases) and subscriptions
10. Revenue by age group

### 3. Dashboard (Power BI)
Interactive dashboard in [`Customer Behavior Dashboard.pbix`](Customer%20Behavior%20Dashboard.pbix) with KPI cards (3.9K customers, $59.76 average purchase, 3.75 average rating), subscription split, revenue and sales by category and by age group, and slicers for subscription status, gender, category and shipping type.
<img width="645" height="421" alt="image" src="https://github.com/user-attachments/assets/ee047d0e-fcb7-451e-8d2e-b495560576f6" />


## Key Findings

| Area | Result |
|---|---|
| **Total revenue** | $233,081 across 3,900 purchases |
| **Gender** | Male customers generated $157,890 vs. $75,191 from female customers. Average spend per purchase is nearly identical (about $59.54 vs. $60.25), so the gap comes from customer count (2,652 vs. 1,248), not spending. |
| **Subscriptions** | 1,053 subscribers (27%) vs. 2,847 non-subscribers. Average spend is almost the same ($59.49 vs. $59.87), so subscription alone is not yet driving higher spend. |
| **Shipping** | Express orders average $60.48 vs. $58.46 for Standard. |
| **Segments** | 3,116 Loyal, 701 Returning and 83 New customers, so the base is heavily repeat-driven. |
| **Repeat buyers** | Of customers with more than 5 purchases, 958 are subscribers and 2,518 are not (about 28% subscribe, close to the overall 27%), so repeat buying does not translate into subscribing. |
| **Age groups** | Revenue is fairly balanced: Young Adult $62,143, Middle-aged $59,197, Adult $55,978, Senior $55,763. |
| **Categories** | Clothing is the largest category (1,737 of 3,900 purchases) and leads revenue, followed by Accessories, Footwear and Outerwear. |
| **Discount-dependent items** | Hat (50.0%), Sneakers (49.7%), Coat (49.1%), Sweater (48.2%), Pants (47.4%) |
| **Top-rated items** | Gloves (3.86), Sandals (3.84), Boots (3.82), Hat (3.80), Skirt (3.78) |

---

## Business Recommendations

- **Boost subscriptions:** add exclusive subscriber benefits, since subscribers currently spend no more than non-subscribers and repeat buyers are not converting.
- **Loyalty programs:** reward repeat buyers to keep them in the Loyal segment.
- **Review discount policy:** several products are bought with a discount about half the time, so balance sales lift against margin.
- **Product positioning:** feature top-rated and best-selling items in campaigns.
- **Targeted marketing:** focus on high-revenue age groups and Express-shipping users.

---

## Repository Structure

```
Customer-Behavior-Analysis/
├── customer_shopping_behavior.csv            # Raw dataset
├── pg sql.sql                                # PostgreSQL analysis queries
├── Customer Behavior Dashboard.pbix          # Power BI dashboard
├── Customer Shopping Behavior Analysis.pdf   # Project report
├── Customer-Shopping-Behavior-Analysis.pptx  # Stakeholder presentation
├── Business Problem  Document.pdf           # Problem statement
└── README.md
```

---

## How to Reproduce

1. **Clean the data:** run the Python preparation steps above on `customer_shopping_behavior.csv` and write the result to a PostgreSQL table.
2. **Run the analysis:** open `pg sql.sql` in pgAdmin or `psql` and execute the queries against that table.
3. **Explore the dashboard:** open the `.pbix` file in Power BI Desktop.

**Requirements:** Python 3 with `pandas`, PostgreSQL, Power BI Desktop.

---

## Author

**Vedika Lohiya**
[LinkedIn](https://www.linkedin.com/in/vedika2203) | [GitHub](https://github.com/vedikalohiya) | vedika.lohiyacse@gmail.com
