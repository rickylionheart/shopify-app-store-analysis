# shopify-app-store-analysis
Sprint 5: Visualize data with Power BI



## Analyst Memo — Shopify App Store Insights

**Dashboard:** Shopify App Store Analysis  
**Reporting Period:** Latest available data  

---

### Key Insight
Analysis of review trends and merchant ratings reveals that developer engagement significantly impacts merchant satisfaction. App categories with higher developer reply rates (`has_developer_reply`) consistently demonstrate stronger average ratings and increased review volume growth over time. Additionally, apps offering free plans see significantly higher adoption and review activity compared to paid-only apps.

---

### Business Impact
* **Merchant Trust & Retention:** Developers who actively respond to reviews foster higher merchant trust, leading to better store app retention and improved app store marketplace health.
* **Category Performance:** High-performing categories (e.g., Marketing, Store Design) drive the majority of review activity, while underserved categories lack sufficient developer competition or engagement.

---

### Recommendation
1. **Incentivize Developer Engagement:** Prompt developers to respond to merchant reviews by providing reply notifications in the Shopify Developer Dashboard.
2. **Promote Free Plan/Trial Models:** Highlight apps with free tiers or trial periods to boost merchant adoption in lower-performing categories.
3. **Featured Marketplace Categories:** Focus marketplace promotions on high-rating, high-reply categories to maximize overall merchant satisfaction.

---

## Technical Details & Data Model

### Data Architecture
The data model follows a classic **Star Schema**:
* **`dim_date`**: Central date table constructed using DAX (`CALENDAR()`).
* **`apps`**: Dimension table containing app metadata, developer details, categories, and pricing.
* **`reviews`**: Fact table capturing customer ratings, review posting dates, and developer reply flags.

### Data Cleaning (Power Query)
* Trimmed whitespace in `app_name` and `developer`.
* Imputed missing developer names with `"Unknown Developer"`.
* Standardized casing in `category_name` to Title Case.
* Removed duplicate reviews based on `review_id`.
* Filtered valid ratings between 1 and 5.
* Converted `has_developer_reply` to numeric values (`1` / `0`) for KPI aggregation.

---

## Repository Structure
