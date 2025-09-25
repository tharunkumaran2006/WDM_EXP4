### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 23-09-2025
### AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
### Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

### Program 1:
```python
import pandas as pd
df = pd.read_csv("/clustervisitor.csv")
print(df)
cluster = {"Young": (df['Age'] <= 30), "Middle": ((df['Age'] > 30) & (df['Age'] <= 50)), "Old": (df['Age'] > 50)}
count = []
for g, c in cluster.items():
  visitors = df[c]
  count.append(len(visitors))
  print(f"Visitors in {g} Group")
  print(visitors)
  print(count)
```


### Output:

<img width="703" height="685" alt="Screenshot 2025-09-24 191531" src="https://github.com/user-attachments/assets/e0e7b2c1-d1f0-4163-96fa-d1ac2d09a658" />



### Visualization:
```python
import matplotlib.pyplot as plt
plt.figure(figsize=(8, 6))
plt.bar(cluster.keys(), count, color='skyblue')
plt.xlabel('Age Groups')
plt.ylabel('Number of Visitors')
plt.title('Visitor Distribution Across Age Groups')
plt.show()
```
### Output:

<img width="960" height="569" alt="Screenshot 2025-09-24 191541" src="https://github.com/user-attachments/assets/07a075e6-c302-430f-bdac-3d57ad9255df" />


## Program 2:
```python
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans
df=pd.read_csv("/clustervisitor (Salary).csv")
df
sc=StandardScaler()
df1=df['Age']
df2=df['Salary']
df3=pd.concat([df1,df2],axis=1)
newdf=sc.fit_transform(df3)
newdf
newdf=sc.fit_transform(df[['Age','Salary']])
newdf
kmeans=KMeans(n_clusters=3,random_state=42)
df3['cluster']=kmeans.fit_predict(newdf)
df3
```
## Output:
<img width="732" height="716" alt="Screenshot 2025-09-24 191600" src="https://github.com/user-attachments/assets/d7bbffa0-5912-4e20-8ea4-9acc4c6ba4e1" />

## Visualisation:
```python
plt.scatter(df3['Age'],df3['Salary'],c=df3['cluster'])
plt.xlabel('Age')
plt.ylabel('Salary in thousands')
plt.show()
```
## Output:

<img width="745" height="438" alt="Screenshot 2025-09-24 191934" src="https://github.com/user-attachments/assets/839d195a-855f-48b5-841e-8dc4683e83dc" />


### Result:

Thus the Implementation of Cluster and visitor segmentation for Navigation patterns is executed successfully.
