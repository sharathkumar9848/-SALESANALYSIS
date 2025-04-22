
 # 1.ImportLibraries
 import pandas as pd
 import matplotlib.pyplot as plt
 import seaborn as sns
 # 2. Load Dataset
 df =pd.read_csv("C:\\Users\\Surendra Reddy\\Downloads\\car_price_dataset.csv")
 # 3. Preview and Basic Info
 print(" First 5 rows:")
 print(df.head())
 print("\nℹ Dataset Info:")
 print(df.info())
 print("\n❓ Missing Values:")
 print(df.isnull().sum())
 # Drop missing values
 df.dropna(inplace=True)
 #4.Correlation Heatmap
 plt.figure(figsize=(8, 6))
 sns.heatmap(df.corr(numeric_only=True), annot=True, cmap='coolwarm')
 plt.title("Correlation Heatmap")
 plt.show()
 # 5. Boxplot for Outliers
 sns.boxplot(data=df[['Price', 'Mileage', 'Engine_Size']])
 plt.title("Boxplot of Price, Mileage, and Engine Size")
 plt.show()
 # 6. Basic Graphs
 # Bar Graph: Average Price by Brand
 df.groupby('Brand')['Price'].mean().sort_values(ascending=False).plot(kind='bar', title='Avg Price by
 Brand', color='skyblue')
 plt.ylabel('Average Price')
 plt.xticks(rotation=45)
 plt.tight_layout()
 plt.show()
 # Pie Chart: Transmission Types
 df['Transmission'].value_counts().plot(kind='pie', autopct='%1.1f%%', title='Transmission Types')
 plt.ylabel(')
 plt.tight_layout()
 plt.show()
 # Scatter Plot: Price vs Mileage
 15
sns.scatterplot(data=df, x='Mileage', y='Price', hue='Fuel_Type')
 plt.title('Scatter plot: Price vs Mileage')
 plt.tight_layout()
 plt.show()
 # Pair Plot
 sns.pairplot(df[['Price', 'Year', 'Mileage', 'Engine_Size']])
 plt.suptitle("Pair Plot of Key Features", y=1.02)
 plt.show()
 # Line Chart
 avg_price_by_year = df.groupby('Year')['Price'].mean().sort_index()
 plt.figure(figsize=(10, 6))
 plt.plot(avg_price_by_year.index, avg_price_by_year.values, marker='o', linestyle='-', color='green')
 plt.title('Average Car Price Over the Years')
 plt.xlabel('Year')
 plt.ylabel('Average Price')
 plt.grid(True)
 plt.tight_layout()
 plt.show()
