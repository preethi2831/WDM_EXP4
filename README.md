### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 19/09/2025
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

df=pd.read_csv("C:\\Users\\Preethi\\Downloads\\clustervisitor.csv")
df

cluster={"Young":(df['Age']<=30),"Middle":((df['Age']>30) & (df['Age']<=50)),"Old":(df['Age']>50)}
print(cluster)

count=[]
for g,c in cluster.items():
    visitors=df[c]
    count.append(len(visitors))
    print(f"visitors in {g} Group")
    print(visitors)
    print(count)

import matplotlib.pyplot as plt
plt.figure(figsize=(8, 6))
plt.bar(cluster.keys(), count, color='skyblue')
plt.xlabel('Age Groups')
plt.ylabel('Number of Visitors')
plt.title('Visitor Distribution Across Age Groups')
plt.show()
```
### Output:

<img width="700" height="545" alt="image" src="https://github.com/user-attachments/assets/86412258-26ba-4989-a3ff-5ec3974e7493" />

### Program 2:
```python
df=pd.read_csv("C:\\Users\\Preethi\\Downloads\\clustervisitor (Salary).csv")
df1=df['Age']
df2=df['Salary']
df3=pd.concat([df1,df2],axis=1)
df3

from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans

sc=StandardScaler()
scaleddata=sc.fit_transform(df3)
print(scaleddata)

kmeans=KMeans(n_clusters=3,random_state=42)
df3['cluster']=kmeans.fit_predict(df3)
df3

plt.scatter(df3['Age'],df3['Salary'],c=df3['cluster'])
plt.xlabel("Age")
plt.ylabel("Salary in thousands")
plt.show()
```
### Output:

<img width="589" height="432" alt="image" src="https://github.com/user-attachments/assets/d0cf235a-1f17-4565-a1e7-f7d153b81306" />

### Result:
Successfuly completed.
