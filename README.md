# Mock_MatplotLib

## 1 Problem 1 : https://tinyurl.com/MatplotlibInterviewQuestion
### Travel Data Visualization

This script analyzes and visualizes travel data for the past year. It includes a line plot, a pie chart, and a scatter plot to provide insights into traveler trends, destination popularity, and the relationship between travelers and revenue.

### Code

```python
import pandas as pd
import matplotlib.pyplot as plt

# Load the dataset
file_path = 'travel.csv'  # Update this path if needed
travel_data = pd.read_csv(file_path)

# Ensure the dataset has the expected columns
# Example columns: 'Month', 'Travelers', 'Revenue', 'Destination'
print(travel_data.head())

# Line Plot: Trend of traveler count and revenue over the year
plt.figure(figsize=(10, 6))
plt.plot(travel_data['Month'], travel_data['Travelers'], marker='o', label='Travelers')
plt.plot(travel_data['Month'], travel_data['Revenue'], marker='o', label='Revenue')
plt.title('Monthly Trends of Travelers and Revenue')
plt.xlabel('Month')
plt.ylabel('Count/Revenue')
plt.legend()
plt.grid(True)
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

# Pie Chart: Distribution of traveler count among the top 5 destinations
top_destinations = travel_data.groupby('Destination')['Travelers'].sum().nlargest(5)
plt.figure(figsize=(8, 8))
plt.pie(top_destinations, labels=top_destinations.index, autopct='%1.1f%%', startangle=140)
plt.title('Top 5 Destinations by Traveler Count')
plt.tight_layout()
plt.show()

# Scatter Plot: Relationship between travelers and revenue
plt.figure(figsize=(10, 6))
plt.scatter(travel_data['Travelers'], travel_data['Revenue'], color='b', alpha=0.7)
plt.title('Travelers vs. Revenue')
plt.xlabel('Travelers')
plt.ylabel('Revenue')
plt.grid(True)
plt.tight_layout()
plt.show()

