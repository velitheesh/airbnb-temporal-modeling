# Temporal Airbnb Seasonality and Modeling  


## Overview
This project investigates the **temporal dynamics and seasonality of Airbnb markets** across four major U.S. cities:

- **Austin, TX**
- **Chicago, IL**
- **Santa Cruz, CA**
- **Washington, D.C.**

Using **Inside Airbnb** data, we construct a **night-level panel dataset** to analyze seasonal pricing and occupancy trends. We then build predictive models using **XGBoost** and **Feedforward Neural Networks**, with **TensorBoard** used to monitor training behavior and overfitting.

---

## Dataset Acquisition

> **Note:** Raw data files are **not included** in this repository due to size constraints.

To reproduce the analysis:

1. Visit **[Inside Airbnb](http://insideairbnb.com/get-the-data.html)**.
2. Download `listings.csv` and `calendar.csv` for the following snapshots:

| City | Snapshot Dates |
|-----|---------------|
| Austin | March 6, 2025 & December 14, 2024 |
| Chicago | March 11, 2025 & December 18, 2024 |
| Santa Cruz | March 28, 2025 & December 31, 2024 |
| Washington, DC | March 13, 2025 & December 18, 2024 |

3. Place the files into a directory structure that matches the paths specified in the notebook’s data loading section.

---

## Features & Methodology

### **Part 1: Dataset Construction**
- Merge `calendar.csv` and `listings.csv`
- Clean price strings and convert to numeric values
- Engineer temporal features:
  - `month`
  - `day_of_year`
  - `is_weekend`
  - `year`
  - Room type indicators

---

### **Part 2: Seasonality Analysis**
- Monthly price trends by city and room type
- Occupancy probability by month
- Cross-city comparisons of seasonal patterns

---

### **Part 3: Temporal Data Split**
To avoid data leakage, a **strict chronological split** is applied:

- **Training:** January – September  
- **Validation:** October – November  
- **Test:** December – February  

---

### **Part 4: Modeling**
Models are trained for both **regression** and **classification** tasks:

#### Regression
- Predict nightly **price**

#### Classification
- Predict **booking probability**

#### Models Used
- **XGBoost (Gradient Boosted Trees)**
- **Feedforward Neural Networks**

---

### **TensorBoard Integration**
TensorBoard is used to:
- Track training and validation loss
- Detect overfitting
- Compare learning stability across models

---

## Installation & Usage

### Clone the Repository
```bash
https://github.com/velitheesh/airbnb-temporal-modeling.git
 ```

### Install Dependencies
```bash
pip install -r requirements.txt
 ```
## Run the Notebook

1. Open `Extra_Credit_assignment_notebook.ipynb` in **Jupyter Notebook** or **Google Colab**.
2. *(Google Colab only)* Mount Google Drive and update file paths to point to your data directory.
3. Run all cells to:
   - Construct datasets  
   - Generate visualizations  
   - Train models  
   - Log results to **TensorBoard**
## Results Summary

The final write-up within the notebook includes:

- Seasonal insights for each city  
- Performance comparison between **XGBoost** and **Neural Networks**  
- TensorBoard diagnostics on model stability and overfitting  
- Business implications for Airbnb host pricing and revenue management

