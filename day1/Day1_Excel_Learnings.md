# Day 1: Excel Data Sanitization & Cleaning Breakdown

## Overview
Today's focus was on core data sanitization techniques in Microsoft Excel / Google Sheets. Raw business data is almost always messy, containing unexpected trailing spaces, inconsistent capitalization, missing values represented as text, and duplicate records. 

---

## 1. Core Functions & Syntax Learned

### A. `TRIM()`
- **Purpose:** Removes leading spaces, trailing spaces, and extra spaces between words.
- **Syntax:** `=TRIM(text_cell)`
- **Example:** `=TRIM("  John Smith  ")` $ightarrow$ `"John Smith"`
- **Why It Matters:** Hidden spaces cause failed `VLOOKUP`/`XLOOKUP` matches and grouping errors in SQL database imports.

### B. `PROPER()`
- **Purpose:** Capitalizes the first letter of each word and converts all other letters to lowercase (Title Case).
- **Syntax:** `=PROPER(text_cell)`
- **Example:** `=PROPER("MARY JANE")` $ightarrow$ `"Mary Jane"`
- **Why It Matters:** Standardizes customer names and categorical variables for clean reporting and professional dashboard display.

### C. Nesting Functions: `=PROPER(TRIM())`
- **Purpose:** Simultaneously cleans whitespace and fixes casing in a single cell operation.
- **Syntax:** `=PROPER(TRIM(B2))`

---

## 2. Data Cleaning Workflows Executed

### A. Cleaning Dirty Currency & String Missing Values
1. **Find & Replace (`Ctrl + H`):**
   - Replaced raw text currency symbols (`$`) with empty strings to convert text formats to true numeric values.
   - Located non-standard null entries (`N/A`) and replaced them with `0` to prevent formula errors during aggregations (`SUM`, `AVERAGE`).
2. **Cell Formatting:**
   - Changed number formatting from *General* to *Currency (`$`)* for quantitative clarity.

### B. Deduplication
1. **Method:** Used **Data > Remove Duplicates**.
2. **Logic:** Targeted the primary key (`Customer_ID`) to ensure each row represents a unique entity, avoiding overcounting in sales metrics.

---

## 3. Key Takeaway & Business Impact
> "Garbage in, garbage out." 

Data validation at the ingestion level prevents inflated revenue reporting and broken queries down the pipeline. Always clean and audit text data before running calculations or exporting to SQL/Power BI.
