
## Academy of PY


```python
# Well done! Having spent years analyzing financial records for big banks, you've finally scratched your idealistic itch and joined the education sector. In your latest role, you've become the Chief Data Scientist for your city's school district. In this capacity, you'll be helping the  school board and mayor make strategic decisions regarding future school budgets and priorities.

# As a first task, you've been asked to analyze the district-wide standardized test results. You'll be given access to every student's math and reading scores, as well as various information on the schools they attend. Your responsibility is to aggregate the data to and showcase obvious trends in school performance. 

# Your final report should include each of the following:

# **District Summary**

# * Create a high level snapshot (in table form) of the district's key metrics, including:
#   * Total Schools
#   * Total Students
#   * Total Budget
#   * Average Math Score
#   * Average Reading Score
#   * % Passing Math
#   * % Passing Reading
#   * Overall Passing Rate (Average of the above two)

# **School Summary**

# * Create an overview table that summarizes key metrics about each school, including:
#   * School Name
#   * School Type
#   * Total Students
#   * Total School Budget
#   * Per Student Budget
#   * Average Math Score
#   * Average Reading Score
#   * % Passing Math
#   * % Passing Reading
#   * Overall Passing Rate (Average of the above two)

# **Top Performing Schools (By Passing Rate)**

# * Create a table that highlights the top 5 performing schools based on Overall Passing Rate. Include:
#   * School Name
#   * School Type
#   * Total Students
#   * Total School Budget
#   * Per Student Budget
#   * Average Math Score
#   * Average Reading Score
#   * % Passing Math
#   * % Passing Reading
#   * Overall Passing Rate (Average of the above two)

# **Top Performing Schools (By Passing Rate)**

# * Create a table that highlights the bottom 5 performing schools based on Overall Passing Rate. Include all of the same metrics as above.

# **Math Scores by Grade**

# * Create a table that lists the average Math Score for students of each grade level (9th, 10th, 11th, 12th) at each school.

# **Reading Scores by Grade**

# * Create a table that lists the average Reading Score for students of each grade level (9th, 10th, 11th, 12th) at each school.

# **Scores by School Spending**

# * Create a table that breaks down school performances based on average Spending Ranges (Per Student). 
#.    Use4 reasonable bins to group school spending. Include in the table each of the following:
#   * Average Math Score
#   * Average Reading Score
#   * % Passing Math
#   * % Passing Reading
#   * Overall Passing Rate (Average of the above two)

# **Scores by School Size**

# * Repeat the above breakdown, but this time group schools based on a reasonable approximation of school size (Small, Medium, Large).

# **Scores by School Type**

# * Repeat the above breakdown, but this time group schools based on school type (Charter vs. District).

# As final considerations:

# * Your script must work for both data-sets given.
# * You must use the Pandas Library and the Jupyter Notebook.
# * You must submit a link to your Jupyter Notebook with the viewable Data Frames. 
# * You must include an exported markdown version of your Notebook called  `README.md` in your GitHub repository.  
# * You must include a written description of three observable trends based on the data. 
# * See [Example Solution](PyCitySchools/PyCitySchools_Example.pdf) for a reference on the expected format. 

# ## Hints and Considerations

# * These are challenging activities for a number of reasons. For one, these activities will require you to analyze thousands of records. Hacking through the data to look for obvious trends in Excel is just not a feasible option. The size of the data may seem daunting, but Python Pandas will allow you to efficiently parse through it. 

# * Second, these activities will also challenge you by requiring you to learn on your feet. Don't fool yourself into thinking: "I need to study Pandas more closely before diving in." Get the basic gist of the library and then _immediately_ get to work. When facing a daunting task, it's easy to think: "I'm just not ready to tackle it yet." But that's the surest way to never succeed. Learning to program requires one to constantly tinker, experiment, and learn on the fly. You are doing exactly the _right_ thing, if you find yourself constantly practicing Google-Fu and diving into documentation. There is just no way (or reason) to try and memorize it all. Online references are available for you to use when you need them. So use them!

# * Take each of these tasks one at a time. Begin your work, answering the basic questions: "How do I import the data?" "How do I convert the data into a DataFrame?" "How do I build the first table?" Don't get intimidated by the number of asks. Many of them are repetitive in nature with just a few tweaks. Be persistent and creative!

# * Expect these exercises to take time! Don't get discouraged if you find yourself spending  hours initially with little progress. Force yourself to deal with the discomfort of not knowing and forge ahead. This exercise is likely to take between 15-30 hours of your time. Consider these hours an investment in your future!

# * As always, feel encouraged to work in groups and get help from your TAs and Instructor. Just remember, true success comes from mastery and _not_ a completed homework assignment. So challenge yourself to truly succeed! 
```


```python
# OBSERVED TREND 1 Narrative
# OBSERVED TREND 2 Narrative
# OBSERVED TREND 3 Narrative
```


```python
import pandas as pd
import numpy as np
```


```python
schools_csv = "schools_complete.csv"
students_csv = "students_complete.csv"
```


```python
# Useful 
# Remember that == is for boolean and = is to set a value
# table_name = pd.DataFrame({"":[],"":[],"":[],"":[],"":[],"":[],"":[],"":[],"":[],"":[],"":[],"":[]})
```


```python
# STUDENTS - read csv as pandas dataframe
df_stu = pd.read_csv(students_csv)
df_stu.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Student ID</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>school</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>66</td>
      <td>79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>94</td>
      <td>61</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>90</td>
      <td>60</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>67</td>
      <td>58</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>97</td>
      <td>84</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_stu.columns
```




    Index(['Student ID', 'name', 'gender', 'grade', 'school', 'reading_score',
           'math_score'],
          dtype='object')




```python
# Re-name header labels
df_stu.columns = ['Student ID', 'Name', 'Gender', 'Grade', 'School', 'Reading_Score', 'Math_Score']
```


```python
df_stu.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Student ID</th>
      <th>Name</th>
      <th>Gender</th>
      <th>Grade</th>
      <th>School</th>
      <th>Reading_Score</th>
      <th>Math_Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>66</td>
      <td>79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>94</td>
      <td>61</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>90</td>
      <td>60</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>67</td>
      <td>58</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>97</td>
      <td>84</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_stu.dtypes
```




    Student ID        int64
    Name             object
    Gender           object
    Grade            object
    School           object
    Reading_Score     int64
    Math_Score        int64
    dtype: object




```python
df_stu.shape
```




    (39170, 7)




```python
df_stu.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Student ID</th>
      <th>Reading_Score</th>
      <th>Math_Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>39170.000000</td>
      <td>39170.00000</td>
      <td>39170.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>19584.500000</td>
      <td>81.87784</td>
      <td>78.985371</td>
    </tr>
    <tr>
      <th>std</th>
      <td>11307.549359</td>
      <td>10.23958</td>
      <td>12.309968</td>
    </tr>
    <tr>
      <th>min</th>
      <td>0.000000</td>
      <td>63.00000</td>
      <td>55.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>9792.250000</td>
      <td>73.00000</td>
      <td>69.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>19584.500000</td>
      <td>82.00000</td>
      <td>79.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>29376.750000</td>
      <td>91.00000</td>
      <td>89.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>39169.000000</td>
      <td>99.00000</td>
      <td>99.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
# SCHOOLS - read csv as pandas dataframe
df_sch = pd.read_csv(schools_csv)
df_sch.head(15)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>name</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Shelton High School</td>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Hernandez High School</td>
      <td>District</td>
      <td>4635</td>
      <td>3022020</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Griffin High School</td>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>Wilson High School</td>
      <td>Charter</td>
      <td>2283</td>
      <td>1319574</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>Cabrera High School</td>
      <td>Charter</td>
      <td>1858</td>
      <td>1081356</td>
    </tr>
    <tr>
      <th>7</th>
      <td>7</td>
      <td>Bailey High School</td>
      <td>District</td>
      <td>4976</td>
      <td>3124928</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8</td>
      <td>Holden High School</td>
      <td>Charter</td>
      <td>427</td>
      <td>248087</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9</td>
      <td>Pena High School</td>
      <td>Charter</td>
      <td>962</td>
      <td>585858</td>
    </tr>
    <tr>
      <th>10</th>
      <td>10</td>
      <td>Wright High School</td>
      <td>Charter</td>
      <td>1800</td>
      <td>1049400</td>
    </tr>
    <tr>
      <th>11</th>
      <td>11</td>
      <td>Rodriguez High School</td>
      <td>District</td>
      <td>3999</td>
      <td>2547363</td>
    </tr>
    <tr>
      <th>12</th>
      <td>12</td>
      <td>Johnson High School</td>
      <td>District</td>
      <td>4761</td>
      <td>3094650</td>
    </tr>
    <tr>
      <th>13</th>
      <td>13</td>
      <td>Ford High School</td>
      <td>District</td>
      <td>2739</td>
      <td>1763916</td>
    </tr>
    <tr>
      <th>14</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_sch.columns
```




    Index(['School ID', 'name', 'type', 'size', 'budget'], dtype='object')




```python
# Re-name Header labels
df_sch.columns = ['School ID', 'School', 'Type', 'Size', 'Budget']
df_sch.columns
```




    Index(['School ID', 'School', 'Type', 'Size', 'Budget'], dtype='object')




```python
df_sch.head(20)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>School</th>
      <th>Type</th>
      <th>Size</th>
      <th>Budget</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Shelton High School</td>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Hernandez High School</td>
      <td>District</td>
      <td>4635</td>
      <td>3022020</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Griffin High School</td>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>Wilson High School</td>
      <td>Charter</td>
      <td>2283</td>
      <td>1319574</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>Cabrera High School</td>
      <td>Charter</td>
      <td>1858</td>
      <td>1081356</td>
    </tr>
    <tr>
      <th>7</th>
      <td>7</td>
      <td>Bailey High School</td>
      <td>District</td>
      <td>4976</td>
      <td>3124928</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8</td>
      <td>Holden High School</td>
      <td>Charter</td>
      <td>427</td>
      <td>248087</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9</td>
      <td>Pena High School</td>
      <td>Charter</td>
      <td>962</td>
      <td>585858</td>
    </tr>
    <tr>
      <th>10</th>
      <td>10</td>
      <td>Wright High School</td>
      <td>Charter</td>
      <td>1800</td>
      <td>1049400</td>
    </tr>
    <tr>
      <th>11</th>
      <td>11</td>
      <td>Rodriguez High School</td>
      <td>District</td>
      <td>3999</td>
      <td>2547363</td>
    </tr>
    <tr>
      <th>12</th>
      <td>12</td>
      <td>Johnson High School</td>
      <td>District</td>
      <td>4761</td>
      <td>3094650</td>
    </tr>
    <tr>
      <th>13</th>
      <td>13</td>
      <td>Ford High School</td>
      <td>District</td>
      <td>2739</td>
      <td>1763916</td>
    </tr>
    <tr>
      <th>14</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_sch.dtypes
```




    School ID     int64
    School       object
    Type         object
    Size          int64
    Budget        int64
    dtype: object




```python
df_sch.shape
```




    (15, 5)




```python
df_sch.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>Size</th>
      <th>Budget</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>15.000000</td>
      <td>15.000000</td>
      <td>1.500000e+01</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>7.000000</td>
      <td>2611.333333</td>
      <td>1.643295e+06</td>
    </tr>
    <tr>
      <th>std</th>
      <td>4.472136</td>
      <td>1420.915282</td>
      <td>9.347763e+05</td>
    </tr>
    <tr>
      <th>min</th>
      <td>0.000000</td>
      <td>427.000000</td>
      <td>2.480870e+05</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>3.500000</td>
      <td>1698.000000</td>
      <td>1.046265e+06</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>7.000000</td>
      <td>2283.000000</td>
      <td>1.319574e+06</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>10.500000</td>
      <td>3474.000000</td>
      <td>2.228999e+06</td>
    </tr>
    <tr>
      <th>max</th>
      <td>14.000000</td>
      <td>4976.000000</td>
      <td>3.124928e+06</td>
    </tr>
  </tbody>
</table>
</div>



# District Summary


```python
# District Summary  - Get data 
# THIS IS A ONE LINE SUMMARY DATA FRAME:
# One line of data for:
# Create a high level snapshot (in table form) of the district's key metrics, including:

# Total Schools
tot_sch = df_sch.School.count()

# Total Students in Schools 
tot_stu = df_sch.Size.sum()

# Total Budget in Schools
tot_bud = df_sch.Budget.sum()

# Average Math Score from Students # returns boolean for all (True and False)
ave_mathscores_all = df_stu.Math_Score.mean() 

# Average Reading Score
ave_readscores_all = df_stu.Reading_Score.mean()

# % Passing Math - Based on 70% or better; how many passed/total studen
passing_math = df_stu.Math_Score.between(70,100, inclusive=True) # Returns boolean of all in selected, 
df_stu[passing_math]

dfmp = df_stu[passing_math]
perc_pass_math = (dfmp.Math_Score.count()/tot_stu) * 100

# % Passing Reading - Base on 70% or better
passing_reading = df_stu.Reading_Score.between(70,100, inclusive=True) # Returns boolean of all in selected, 

dfrp = df_stu[passing_reading]
perc_pass_reading = (dfrp.Reading_Score.count()/tot_stu) * 100

#   * Overall Passing Rate (Average of the above two)  - average of those s
overall_pass_rate = (perc_pass_math + perc_pass_reading)/2

# Create Table - District Summary# DISTRICT SUMMARY
district_summary = pd.DataFrame({"Total Schools":[tot_sch],"Total Students":[tot_stu],"Total Budget":[tot_bud],
                                 "Average Math Score":[ave_mathscores_all],"Average Reading Score":[ave_readscores_all],
                                 "% Passing Math":[perc_pass_math],"% Passing Reading":[perc_pass_reading],"Overall Passing Rate":[overall_pass_rate]})

# Create Table - District Summary
district_summary = district_summary[["Total Schools","Total Students","Total Budget","Average Math Score","Average Reading Score","% Passing Math","% Passing Reading","Overall Passing Rate"]]
# Need to format $ for budget
district_summary["Total Budget"] = district_summary["Total Budget"].map("${:,.2f}".format)
district_summary
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Total Schools</th>
      <th>Total Students</th>
      <th>Total Budget</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>Overall Passing Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>15</td>
      <td>39170</td>
      <td>$24,649,428.00</td>
      <td>78.985371</td>
      <td>81.87784</td>
      <td>74.980853</td>
      <td>85.805463</td>
      <td>80.393158</td>
    </tr>
  </tbody>
</table>
</div>




```python
## merge data sets df_stu & df_sch
merge_data = pd.merge(df_sch, df_stu, on=('School'))
merge_data.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>School</th>
      <th>Type</th>
      <th>Size</th>
      <th>Budget</th>
      <th>Student ID</th>
      <th>Name</th>
      <th>Gender</th>
      <th>Grade</th>
      <th>Reading_Score</th>
      <th>Math_Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>66</td>
      <td>79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>94</td>
      <td>61</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>90</td>
      <td>60</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>67</td>
      <td>58</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>97</td>
      <td>84</td>
    </tr>
  </tbody>
</table>
</div>



# School Summary



```python
# School Summary - Get data from 
# school is df_sch 
# student is df_stu
# merge_data us combined data files

# Get Name school Type values
sch_type = df_sch.set_index(["School"])["Type"]

# Get student count per school
tot_sch_stu = merge_data["School"].value_counts()

# Get Total per School Budget
tot_sch_bud = merge_data.groupby(["School"]).mean()["Budget"]

# Compute per Student Budget
stu_bud = tot_sch_bud/tot_sch_stu

# Get Average Math and Reading scores per school
ave_math_score = merge_data.groupby(["School"]).mean()["Math_Score"]
ave_reading_score = merge_data.groupby(["School"]).mean()["Reading_Score"]

# Compute Percent Passing for Math and Reading
sch_perc_pass_math = merge_data[merge_data["Math_Score"] >= 70].groupby("School").count()["Name"] #/tot_stu) * 100
sch_perc_pass_math =(sch_perc_pass_math/tot_sch_stu) * 100
sch_perc_pass_reading = merge_data[merge_data["Reading_Score"] >= 70].groupby("School").count()["Name"]
sch_perc_pass_reading = (sch_perc_pass_reading/tot_sch_stu) * 100

# Overall Passing Rate (Average of the above two)  - average of those s
over_pass_rate = (sch_perc_pass_math + sch_perc_pass_reading)/2

# Create Table - School Summary
school_summary = pd.DataFrame({"School Type": sch_type, "Total Students": tot_sch_stu, "Total School Budget": tot_sch_bud, "Per Student Budget": stu_bud, "Average Math Score": ave_math_score, "Average Reading Score": ave_reading_score, "% Passing Math": sch_perc_pass_math, "% Passing Reading": sch_perc_pass_reading, "Overall Passing Rate": over_pass_rate})
school_summary = school_summary[["School Type","Total Students","Total School Budget","Per Student Budget", "Average Math Score","Average Reading Score","% Passing Math","% Passing Reading","Overall Passing Rate"]]

# Format columns where needed
school_summary["Total School Budget"] = school_summary["Total School Budget"].map("${:,.2f}".format)
school_summary["Per Student Budget"] = school_summary["Per Student Budget"].map("${:,.2f}".format)
school_summary

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School Type</th>
      <th>Total Students</th>
      <th>Total School Budget</th>
      <th>Per Student Budget</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>Overall Passing Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>District</td>
      <td>4976</td>
      <td>$3,124,928.00</td>
      <td>$628.00</td>
      <td>77.048432</td>
      <td>81.033963</td>
      <td>66.680064</td>
      <td>81.933280</td>
      <td>74.306672</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>Charter</td>
      <td>1858</td>
      <td>$1,081,356.00</td>
      <td>$582.00</td>
      <td>83.061895</td>
      <td>83.975780</td>
      <td>94.133477</td>
      <td>97.039828</td>
      <td>95.586652</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>District</td>
      <td>2949</td>
      <td>$1,884,411.00</td>
      <td>$639.00</td>
      <td>76.711767</td>
      <td>81.158020</td>
      <td>65.988471</td>
      <td>80.739234</td>
      <td>73.363852</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>District</td>
      <td>2739</td>
      <td>$1,763,916.00</td>
      <td>$644.00</td>
      <td>77.102592</td>
      <td>80.746258</td>
      <td>68.309602</td>
      <td>79.299014</td>
      <td>73.804308</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>Charter</td>
      <td>1468</td>
      <td>$917,500.00</td>
      <td>$625.00</td>
      <td>83.351499</td>
      <td>83.816757</td>
      <td>93.392371</td>
      <td>97.138965</td>
      <td>95.265668</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>District</td>
      <td>4635</td>
      <td>$3,022,020.00</td>
      <td>$652.00</td>
      <td>77.289752</td>
      <td>80.934412</td>
      <td>66.752967</td>
      <td>80.862999</td>
      <td>73.807983</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>Charter</td>
      <td>427</td>
      <td>$248,087.00</td>
      <td>$581.00</td>
      <td>83.803279</td>
      <td>83.814988</td>
      <td>92.505855</td>
      <td>96.252927</td>
      <td>94.379391</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>District</td>
      <td>2917</td>
      <td>$1,910,635.00</td>
      <td>$655.00</td>
      <td>76.629414</td>
      <td>81.182722</td>
      <td>65.683922</td>
      <td>81.316421</td>
      <td>73.500171</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>District</td>
      <td>4761</td>
      <td>$3,094,650.00</td>
      <td>$650.00</td>
      <td>77.072464</td>
      <td>80.966394</td>
      <td>66.057551</td>
      <td>81.222432</td>
      <td>73.639992</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>Charter</td>
      <td>962</td>
      <td>$585,858.00</td>
      <td>$609.00</td>
      <td>83.839917</td>
      <td>84.044699</td>
      <td>94.594595</td>
      <td>95.945946</td>
      <td>95.270270</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>District</td>
      <td>3999</td>
      <td>$2,547,363.00</td>
      <td>$637.00</td>
      <td>76.842711</td>
      <td>80.744686</td>
      <td>66.366592</td>
      <td>80.220055</td>
      <td>73.293323</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>Charter</td>
      <td>1761</td>
      <td>$1,056,600.00</td>
      <td>$600.00</td>
      <td>83.359455</td>
      <td>83.725724</td>
      <td>93.867121</td>
      <td>95.854628</td>
      <td>94.860875</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>Charter</td>
      <td>1635</td>
      <td>$1,043,130.00</td>
      <td>$638.00</td>
      <td>83.418349</td>
      <td>83.848930</td>
      <td>93.272171</td>
      <td>97.308869</td>
      <td>95.290520</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>Charter</td>
      <td>2283</td>
      <td>$1,319,574.00</td>
      <td>$578.00</td>
      <td>83.274201</td>
      <td>83.989488</td>
      <td>93.867718</td>
      <td>96.539641</td>
      <td>95.203679</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>Charter</td>
      <td>1800</td>
      <td>$1,049,400.00</td>
      <td>$583.00</td>
      <td>83.682222</td>
      <td>83.955000</td>
      <td>93.333333</td>
      <td>96.611111</td>
      <td>94.972222</td>
    </tr>
  </tbody>
</table>
</div>



# Top Performing Schools (By Passing Rate)


```python
# **Top Performing Schools (By Passing Rate)**

# Resort and take 5
# Create Table - Top Performing Schools (By Passing Rate)
top_schools = school_summary.sort_values(["Overall Passing Rate"], ascending = False).head(5)                                         
top_schools                                                                
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School Type</th>
      <th>Total Students</th>
      <th>Total School Budget</th>
      <th>Per Student Budget</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>Overall Passing Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Cabrera High School</th>
      <td>Charter</td>
      <td>1858</td>
      <td>$1,081,356.00</td>
      <td>$582.00</td>
      <td>83.061895</td>
      <td>83.975780</td>
      <td>94.133477</td>
      <td>97.039828</td>
      <td>95.586652</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>Charter</td>
      <td>1635</td>
      <td>$1,043,130.00</td>
      <td>$638.00</td>
      <td>83.418349</td>
      <td>83.848930</td>
      <td>93.272171</td>
      <td>97.308869</td>
      <td>95.290520</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>Charter</td>
      <td>962</td>
      <td>$585,858.00</td>
      <td>$609.00</td>
      <td>83.839917</td>
      <td>84.044699</td>
      <td>94.594595</td>
      <td>95.945946</td>
      <td>95.270270</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>Charter</td>
      <td>1468</td>
      <td>$917,500.00</td>
      <td>$625.00</td>
      <td>83.351499</td>
      <td>83.816757</td>
      <td>93.392371</td>
      <td>97.138965</td>
      <td>95.265668</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>Charter</td>
      <td>2283</td>
      <td>$1,319,574.00</td>
      <td>$578.00</td>
      <td>83.274201</td>
      <td>83.989488</td>
      <td>93.867718</td>
      <td>96.539641</td>
      <td>95.203679</td>
    </tr>
  </tbody>
</table>
</div>



# Bottom Performing Schools (By Passing Rate)


```python
# * Create a table that highlights the bottom 5 performing schools based on Overall Passing Rate. Include all of the same metrics as above.
# Re-sort and take 5

# Create Table - Bottom Performing Schools (By Passing Rate)
bottom_schools = school_summary.sort_values(["Overall Passing Rate"], ascending = True).head(5)                                         
bottom_schools     
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School Type</th>
      <th>Total Students</th>
      <th>Total School Budget</th>
      <th>Per Student Budget</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>Overall Passing Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Rodriguez High School</th>
      <td>District</td>
      <td>3999</td>
      <td>$2,547,363.00</td>
      <td>$637.00</td>
      <td>76.842711</td>
      <td>80.744686</td>
      <td>66.366592</td>
      <td>80.220055</td>
      <td>73.293323</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>District</td>
      <td>2949</td>
      <td>$1,884,411.00</td>
      <td>$639.00</td>
      <td>76.711767</td>
      <td>81.158020</td>
      <td>65.988471</td>
      <td>80.739234</td>
      <td>73.363852</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>District</td>
      <td>2917</td>
      <td>$1,910,635.00</td>
      <td>$655.00</td>
      <td>76.629414</td>
      <td>81.182722</td>
      <td>65.683922</td>
      <td>81.316421</td>
      <td>73.500171</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>District</td>
      <td>4761</td>
      <td>$3,094,650.00</td>
      <td>$650.00</td>
      <td>77.072464</td>
      <td>80.966394</td>
      <td>66.057551</td>
      <td>81.222432</td>
      <td>73.639992</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>District</td>
      <td>2739</td>
      <td>$1,763,916.00</td>
      <td>$644.00</td>
      <td>77.102592</td>
      <td>80.746258</td>
      <td>68.309602</td>
      <td>79.299014</td>
      <td>73.804308</td>
    </tr>
  </tbody>
</table>
</div>



# Math Scores by Grade


```python
# **Math Scores by Grade**

# Get Average values per grade for all students, grouped by school
m_nineth_score = merge_data[merge_data["Grade"] == "9th"].groupby("School").mean()["Math_Score"]
m_tenth_score = merge_data[merge_data["Grade"] == "10th"].groupby("School").mean()["Math_Score"]
m_eleventh_score = merge_data[merge_data["Grade"] == "11th"].groupby("School").mean()["Math_Score"]
m_twelfth_score = merge_data[merge_data["Grade"] == "12th"].groupby("School").mean()["Math_Score"]

# Create Table - Math Scores by Grade
df_ms_by_grade = pd.DataFrame({"9th":m_nineth_score,"10th":m_tenth_score,"11th":m_eleventh_score,"12th":m_twelfth_score})
ms_by_grade = df_ms_by_grade[["9th","10th","11th","12th"]]
ms_by_grade
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>9th</th>
      <th>10th</th>
      <th>11th</th>
      <th>12th</th>
    </tr>
    <tr>
      <th>School</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>77.083676</td>
      <td>76.996772</td>
      <td>77.515588</td>
      <td>76.492218</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>83.094697</td>
      <td>83.154506</td>
      <td>82.765560</td>
      <td>83.277487</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>76.403037</td>
      <td>76.539974</td>
      <td>76.884344</td>
      <td>77.151369</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>77.361345</td>
      <td>77.672316</td>
      <td>76.918058</td>
      <td>76.179963</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>82.044010</td>
      <td>84.229064</td>
      <td>83.842105</td>
      <td>83.356164</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>77.438495</td>
      <td>77.337408</td>
      <td>77.136029</td>
      <td>77.186567</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>83.787402</td>
      <td>83.429825</td>
      <td>85.000000</td>
      <td>82.855422</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>77.027251</td>
      <td>75.908735</td>
      <td>76.446602</td>
      <td>77.225641</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>77.187857</td>
      <td>76.691117</td>
      <td>77.491653</td>
      <td>76.863248</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>83.625455</td>
      <td>83.372000</td>
      <td>84.328125</td>
      <td>84.121547</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>76.859966</td>
      <td>76.612500</td>
      <td>76.395626</td>
      <td>77.690748</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>83.420755</td>
      <td>82.917411</td>
      <td>83.383495</td>
      <td>83.778976</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>83.590022</td>
      <td>83.087886</td>
      <td>83.498795</td>
      <td>83.497041</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>83.085578</td>
      <td>83.724422</td>
      <td>83.195326</td>
      <td>83.035794</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>83.264706</td>
      <td>84.010288</td>
      <td>83.836782</td>
      <td>83.644986</td>
    </tr>
  </tbody>
</table>
</div>



# Reading Scores by Grade


```python
# **Reading Scores by Grade**

# Get Average values per grade for all students, grouped by school
r_nineth_score = merge_data[merge_data["Grade"] == "9th"].groupby("School").mean()["Math_Score"]
r_tenth_score = merge_data[merge_data["Grade"] == "10th"].groupby("School").mean()["Math_Score"]
r_eleventh_score = merge_data[merge_data["Grade"] == "11th"].groupby("School").mean()["Math_Score"]
r_twelfth_score = merge_data[merge_data["Grade"] == "12th"].groupby("School").mean()["Math_Score"]

# Create Table - Reading Scores by Grade
df_rs_by_grade = pd.DataFrame({"9th":r_nineth_score,"10th":r_tenth_score,"11th":r_eleventh_score,"12th":r_twelfth_score})
rs_by_grade = df_rs_by_grade[["9th","10th","11th","12th"]]

rs_by_grade
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>9th</th>
      <th>10th</th>
      <th>11th</th>
      <th>12th</th>
    </tr>
    <tr>
      <th>School</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>77.083676</td>
      <td>76.996772</td>
      <td>77.515588</td>
      <td>76.492218</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>83.094697</td>
      <td>83.154506</td>
      <td>82.765560</td>
      <td>83.277487</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>76.403037</td>
      <td>76.539974</td>
      <td>76.884344</td>
      <td>77.151369</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>77.361345</td>
      <td>77.672316</td>
      <td>76.918058</td>
      <td>76.179963</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>82.044010</td>
      <td>84.229064</td>
      <td>83.842105</td>
      <td>83.356164</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>77.438495</td>
      <td>77.337408</td>
      <td>77.136029</td>
      <td>77.186567</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>83.787402</td>
      <td>83.429825</td>
      <td>85.000000</td>
      <td>82.855422</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>77.027251</td>
      <td>75.908735</td>
      <td>76.446602</td>
      <td>77.225641</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>77.187857</td>
      <td>76.691117</td>
      <td>77.491653</td>
      <td>76.863248</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>83.625455</td>
      <td>83.372000</td>
      <td>84.328125</td>
      <td>84.121547</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>76.859966</td>
      <td>76.612500</td>
      <td>76.395626</td>
      <td>77.690748</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>83.420755</td>
      <td>82.917411</td>
      <td>83.383495</td>
      <td>83.778976</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>83.590022</td>
      <td>83.087886</td>
      <td>83.498795</td>
      <td>83.497041</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>83.085578</td>
      <td>83.724422</td>
      <td>83.195326</td>
      <td>83.035794</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>83.264706</td>
      <td>84.010288</td>
      <td>83.836782</td>
      <td>83.644986</td>
    </tr>
  </tbody>
</table>
</div>



# Scores by School Spending


```python
# **Scores by School Spending**

# Create Bins as required
bin_spend = [0,585,615,645,675]
bin_spend_label = ["<585","585-615","615-645","645-675"]
spend_school_summary = school_summary
# Fill bins
spend_school_summary["Spending Ranges (Per Student)"] = pd.cut(stu_bud, bin_spend, labels = bin_spend_label)
# Get values of average for the columns
sp_ave_mathscore = spend_school_summary.groupby(["Spending Ranges (Per Student)"]).mean()['Average Math Score']
sp_ave_readscore = spend_school_summary.groupby(["Spending Ranges (Per Student)"]).mean()['Average Reading Score']
sp_pass_math =  spend_school_summary.groupby(["Spending Ranges (Per Student)"]).mean()['% Passing Math']
sp_pass_read =  spend_school_summary.groupby(["Spending Ranges (Per Student)"]).mean()['% Passing Reading']
sp_over_pass =  (sp_pass_math + sp_pass_read) / 2

# Create Table - Scores by School Spending 
spendscores = pd.DataFrame({"Average Math Score":sp_ave_mathscore, "Average Reading Score":sp_ave_readscore,
                               "% Passing Math":sp_pass_math,"% Passing Reading":sp_pass_read,
                                    "Overall Passing Rate":sp_over_pass}) 
scores_by_school_spending = spendscores[["Average Math Score", "Average Reading Score",
                               "% Passing Math","% Passing Reading","Overall Passing Rate"]]
scores_by_school_spending
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>Overall Passing Rate</th>
    </tr>
    <tr>
      <th>Spending Ranges (Per Student)</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>&lt;585</th>
      <td>83.455399</td>
      <td>83.933814</td>
      <td>93.460096</td>
      <td>96.610877</td>
      <td>95.035486</td>
    </tr>
    <tr>
      <th>585-615</th>
      <td>83.599686</td>
      <td>83.885211</td>
      <td>94.230858</td>
      <td>95.900287</td>
      <td>95.065572</td>
    </tr>
    <tr>
      <th>615-645</th>
      <td>79.079225</td>
      <td>81.891436</td>
      <td>75.668212</td>
      <td>86.106569</td>
      <td>80.887391</td>
    </tr>
    <tr>
      <th>645-675</th>
      <td>76.997210</td>
      <td>81.027843</td>
      <td>66.164813</td>
      <td>81.133951</td>
      <td>73.649382</td>
    </tr>
  </tbody>
</table>
</div>



# Scores by School Size


```python
# **Scores by School Size**

# Define bins for reasonable school spending ranges on average student spending amounts
# Create Bins as required
bin_size = [0,1000,2000,5000]
bin_size_label = ["Small <1000","Medium (1000-2000)","Large (2000-5000)"] 

# Fill bins
school_summary["School Size"] = pd.cut(school_summary["Total Students"], bin_size, labels = bin_size_label)

# Get values of averages for columns
sz_ave_mathscore = school_summary.groupby(["School Size"]).mean()['Average Math Score']
sz_ave_readscore = school_summary.groupby(["School Size"]).mean()['Average Reading Score']
sz_pass_math =  school_summary.groupby(["School Size"]).mean()['% Passing Math']
sz_pass_read =  school_summary.groupby(["School Size"]).mean()['% Passing Reading']
sz_over_pass =  (sz_pass_math + sz_pass_read) / 2

# Create Table - Scores by School Spending 
spendscores = pd.DataFrame({"Average Math Score":sz_ave_mathscore, "Average Reading Score":sz_ave_readscore,
                               "% Passing Math":sz_pass_math,"% Passing Reading":sz_pass_read,
                                    "Overall Passing Rate":sz_over_pass}) 
scores_by_school_size = spendscores[["Average Math Score", "Average Reading Score",
                               "% Passing Math","% Passing Reading","Overall Passing Rate"]]
scores_by_school_size
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>Overall Passing Rate</th>
    </tr>
    <tr>
      <th>School Size</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Small &lt;1000</th>
      <td>83.821598</td>
      <td>83.929843</td>
      <td>93.550225</td>
      <td>96.099437</td>
      <td>94.824831</td>
    </tr>
    <tr>
      <th>Medium (1000-2000)</th>
      <td>83.374684</td>
      <td>83.864438</td>
      <td>93.599695</td>
      <td>96.790680</td>
      <td>95.195187</td>
    </tr>
    <tr>
      <th>Large (2000-5000)</th>
      <td>77.746417</td>
      <td>81.344493</td>
      <td>69.963361</td>
      <td>82.766634</td>
      <td>76.364998</td>
    </tr>
  </tbody>
</table>
</div>



# Scores by School Type


```python
# **Scores by School Type**

# Get values of averages for columns
st_ave_mathscore = school_summary.groupby(["School Type"]).mean()['Average Math Score']
st_ave_readscore = school_summary.groupby(["School Type"]).mean()['Average Reading Score']
st_pass_math =  school_summary.groupby(["School Type"]).mean()['% Passing Math']
st_pass_read =  school_summary.groupby(["School Type"]).mean()['% Passing Reading']
st_over_pass =  (st_pass_math + st_pass_read) / 2

# Create Table - Scores by School Spending 
typescores = pd.DataFrame({"Average Math Score":st_ave_mathscore, "Average Reading Score":st_ave_readscore,
                               "% Passing Math":st_pass_math,"% Passing Reading":st_pass_read,
                                    "Overall Passing Rate":st_over_pass}) 
scores_by_school_type = typescores[["Average Math Score", "Average Reading Score",
                               "% Passing Math","% Passing Reading","Overall Passing Rate"]]
scores_by_school_type
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>Overall Passing Rate</th>
    </tr>
    <tr>
      <th>School Type</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Charter</th>
      <td>83.473852</td>
      <td>83.896421</td>
      <td>93.620830</td>
      <td>96.586489</td>
      <td>95.103660</td>
    </tr>
    <tr>
      <th>District</th>
      <td>76.956733</td>
      <td>80.966636</td>
      <td>66.548453</td>
      <td>80.799062</td>
      <td>73.673757</td>
    </tr>
  </tbody>
</table>
</div>




```python
# All in a day's work... give or take a few
```
