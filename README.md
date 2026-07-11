# Wholesale Customers Segmentation 🛒

An end-to-end unsupervised machine learning project that segment wholesale distributor clients based on their annual spending across various product categories. By using hierarchical clustering, this project successfully groups clients into actionable business segments to optimize marketing and inventory strategies.

## 📊 Dataset Overview
The dataset is sourced from the **UCI Machine Learning Repository** and contains the annual spending (in monetary units) of 440 clients.

### Features:
* **Product Categories:** `Fresh`, `Milk`, `Grocery`, `Frozen`, `Detergents_Paper`, and `Delicassen`.
* **Structural Attributes:** `Channel` (Hotel/Restaurant/Cafe or Retail) and `Region`.

---

## 🛠️ Project Workflow

### 1. Data Preprocessing & Outlier Handling
* Evaluated data distribution shapes across product categories.
* Checked for zero values to prevent mathematical issues during log calculations.
* Applied a **Log Transformation** (`np.log1p`) to mitigate the skewness caused by high-spending power-buyers (outliers) and stabilize variance.

### 2. Hierarchical Clustering Analysis
* Constructed a **Dendrogram** using **Ward’s Linkage Method** to minimize variance within clusters.
* Evaluated optimal group counts visually and mathematically using **Silhouette Scores**.

| Number of Clusters | Silhouette Score | Status |
|--------------------|------------------|--------|
| **2 Clusters** | **0.3150** | 🏆 **Optimal Choice** |
| 3 Clusters         | 0.2520           | Suboptimal |
| 4 Clusters         | 0.1985           | Suboptimal |

### 3. Model Implementation
* Fitted an `AgglomerativeClustering` model using `n_clusters=2`, `metric='euclidean'`, and `linkage='ward'`.

---

## 📈 Identified Customer Profiles

The clustering algorithm divided the clients into two distinct business profiles based on their spending characteristics:

### 🔹 Cluster 0: High-Volume Bulk Buyers (Supermarkets & Large Retailers)
* **Characteristics:** Massive spending across all retail domains.
* **Key Metrics:** Averaged **16,539** units in `Grocery` and **7,314** units in `Detergents_Paper` (over 7x more than Cluster 1).

### 🔹 Cluster 1: Foodservice Providers (Small Cafes, Restaurants & Hotels)
* **Characteristics:** High fresh ingredient demands but minimal inventory/packaged goods spending.
* **Key Metrics:** Dominated heavily by `Fresh` food purchases (**12,176** units), but exceptionally low spending on `Detergents_Paper` (**970** units).

---

## 💻 Tech Stack & Libraries
* **Python 3**
* **Pandas & NumPy** - Data manipulation and structural transformation
* **Matplotlib & Seaborn** - Dendrogram visualization and scatter-plot clustering insights
* **Scikit-Learn** - Agglomerative Clustering modeling and Silhouette evaluation metrics

---

## 🚀 How to Run the Project
1. Clone the repository:
   ```bash
   git clone [https://github.com/yourusername/wholesale-customer-segmentation.git](https://github.com/yourusername/wholesale-customer-segmentation.git)
