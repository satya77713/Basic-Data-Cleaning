# Basic Data Cleaning Using Python & Pandas

## 📌 Project Overview

This project demonstrates basic data cleaning techniques using Python and Pandas on an Employee dataset.

The main objective is to improve data quality by handling missing values, identifying and removing duplicate records, correcting data types, and removing unnecessary spaces from categorical columns.

This project was completed as part of the **Veda Technology AI & ML Internship – Task 25**.

## 🎯 Project Objectives

- Load and explore the Employee dataset.
- Identify missing values.
- Handle missing values using median and mode.
- Identify duplicate records.
- Remove duplicate entries.
- Convert categorical columns into appropriate data types.
- Verify numerical data types.
- Remove extra spaces from text columns.
- Prepare a cleaned dataset for further analysis.

## 🛠️ Technologies Used

- Python
- Pandas
- NumPy
- Google Colab
- Jupyter Notebook
- CSV Dataset

## 📂 Dataset Information

**Dataset Name:** Employee.csv

The dataset contains employee-related information.

| Column | Description |
|---|---|
| Education | Employee education level |
| JoiningYear | Year of joining |
| City | Employee city |
| PaymentTier | Employee payment tier |
| Age | Employee age |
| Gender | Employee gender |
| EverBenched | Whether employee was ever benched |
| ExperienceInCurrentDomain | Experience in current domain |
| LeaveOrNot | Employee leaving status |

**Dataset size:** 4,653 records and 9 columns.

## ⚙️ Project Workflow

### 1. Import Libraries

```python
import numpy as np
import pandas as pd
```

### 2. Load Dataset

```python
df = pd.read_csv("Employee.csv")
```

### 3. Explore Dataset

```python
df.info()
display(df.head(10))
```

### 4. Check Missing Values

```python
df.isnull().sum()
```

### 5. Handle Missing Values

Numerical columns use median values, while categorical columns use mode values.

```python
for column in df.columns:

    if df[column].isnull().sum() > 0:

        if pd.api.types.is_numeric_dtype(df[column]):
            df[column] = df[column].fillna(
                df[column].median()
            )
        else:
            df[column] = df[column].fillna(
                df[column].mode()[0]
            )
```

### 6. Identify Duplicate Records

```python
df.duplicated().sum()
```

### 7. Remove Duplicate Records

```python
before = len(df)

df = df.drop_duplicates()

after = len(df)

print("Records Before:", before)
print("Records After:", after)
```

### 8. Correct Data Types

Categorical columns are converted into category data types, and numerical columns are verified.

```python
categorical_columns = [
    'Education',
    'City',
    'Gender',
    'EverBenched'
]

for column in categorical_columns:
    df[column] = df[column].astype('category')
```

### 9. Remove Extra Spaces

```python
for column in [
    'Education',
    'City',
    'Gender',
    'EverBenched'
]:
    df[column] = df[column].apply(
        lambda x: x.strip() if isinstance(x, str) else x
    )
```

### 10. Verify Cleaned Dataset

```python
print(df.info())
print(df.isnull().sum())
print(df.duplicated().sum())
```

## 📊 Key Cleaning Techniques

| Technique | Method Used |
|---|---|
| Missing Value Detection | `isnull().sum()` |
| Missing Value Handling | `fillna()` |
| Duplicate Detection | `duplicated()` |
| Duplicate Removal | `drop_duplicates()` |
| Data Type Conversion | `astype()` |
| Numerical Type Verification | `pd.to_numeric()` |
| Text Cleaning | `strip()` |

## 📁 Project Structure

```text
Basic-Data-Cleaning/
│
├── Employee.csv
├── Basic_Data_Cleaning.ipynb
├── Cleaned_Employee_Dataset.csv
└── README.md
```

## 🚀 How to Run the Project

1. Clone the repository:

```bash
git clone https://github.com/satya77713/Basic-Data-Cleaning.git
```

2. Navigate to the project directory:

```bash
cd Basic-Data-Cleaning
```

3. Install the required libraries:

```bash
pip install pandas numpy
```

4. Open Jupyter Notebook:

```bash
jupyter notebook Basic_Data_Cleaning.ipynb
```

5. Make sure Employee.csv is available in the working directory.
6. Run all notebook cells.

## 📚 Key Learnings

- Understanding data quality and preprocessing.
- Handling missing values using Pandas.
- Identifying and removing duplicate records.
- Converting columns into appropriate data types.
- Cleaning unnecessary spaces from text data.
- Exploring and inspecting datasets.
- Preparing datasets for data analysis and machine learning.

## 🎓 Internship Details

- **Organization:** Veda Technology
- **Program:** AI & ML Internship
- **Task:** Basic Data Cleaning
- **Task Number:** 25

## 👨‍💻 Author

**Satya**

GitHub: [@satya77713](https://github.com/satya77713)

## 📝 Conclusion

This project provided practical experience in performing basic data cleaning using Python and Pandas. By applying missing-value handling, duplicate removal, data type correction, and text cleaning techniques, I learned how to improve dataset quality and prepare data for further analysis and machine learning applications.

---

⭐ If you find this project useful, feel free to star the repository!
