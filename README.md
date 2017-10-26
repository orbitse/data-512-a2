# data-512-a2: Bias in Wikipedia Article Data

## Purpose of Project
The goal of this assignment is to explore the concept of 'bias' through data on Wikipedia articles - specifically, articles on political figures from a variety of countries.  

You will combine a dataset of Wikipedia articles with a dataset of country populations, and use a machine learning service called __ORES__ to estimate the quality of each article.  

This project includes an analysis of how the coverage of politicians on Wikipedia and the quality of articles about politicians varies between countries. The analysis will consist of a series of visualizations that show:  
 1.	The countries with the greatest and least coverage of politicians on Wikipedia compared to their population. 
 2.	The countries with the highest and lowest proportion of high quality articles about politicians. 
 
## Data Used in Project

We will be combining three datasets from different sources:  
 - the Wikipedia article dataset,
 - the country population dataset, and
 - the article quality prediction dataset.

### Wikipedia Article Data

This English-language Wikipedia article data is from the "Category:Politicians by nationality" and subcategories. The Wikipedia dataset can be found on [Figshare](https://figshare.com/articles/Untitled_Item/5513449). The article data was extracted via the Wikimedia API and saved as a CSV file named `page_data.csv`. The page_data.csv file is also available in this repository.  
  
The columns in the page_data.csv file are:  
 1. "country", containing the sanitised country name, extracted from the category name;
 2. "page", containing the unsanitised page title.
 3. "last_edit", containing the edit ID of the last edit to the page. 
 
 __Wikipedia Data License__
 
The Wikipedia data and the code used to generate that data are released under the CC-BY-SA 4.0 license.  
 
### Country Population Data 

The country population data comes from the Population Research Bureau [website](http://www.prb.org/DataFinder/Topic/Rankings.aspx?ind=14). If you would like to download the population data, click the Excel icon in the upper right corner, as shown in this screenshot.  
  
![alt text](https://raw.githubusercontent.com/orbitse/data-512-a2/master/population_data.jpeg)  
  
However, the same population data is available in this repository in the CSV file, `Population Mid-2015.csv`.  

__Population Data License__  


### Article Quality Prediction Data 

The predicted quality scores for each article in the Wikipedia dataset comes from a Wikimedia API endpoint for a machine learning system called ORES ("Objective Revision Evaluation Service"). ORES estimates the quality of an article (at a particular point in time), and assigns a series of probabilities that the article is in one of 6 quality categories.  

The range of quality scores are, from best to worst:  
  1.	FA - Featured article
  2.	GA - Good article
  3.	B - B-class article
  4.	C - C-class article
  5.	Start - Start-class article
  6.	Stub - Stub-class article  

These quality scores are a sub-set of quality assessment categories developed by Wikipedia editors. For more information about the scores, see [here](https://en.wikipedia.org/wiki/Wikipedia:WikiProject_assessment#Grades).  

The ORES API documentation can be found [here](https://www.mediawiki.org/wiki/ORES) and the web API is [here](https://ores.wikimedia.org/v3/). The API requires a revision ID, which is the third column in the Wikipedia dataset ("last_edit"), and a model, which is "wp10". 

When you query the API, you will notice that ORES returns a prediction value that contains the name of one category, as well as probability values for each of the 6 quality categories. But, you __only need the prediction value for this analysis__.

`# Example of the JSON format of response from the ORES API`  
`{"enwiki": {`  
`        "models": {`  
`                "wp10": {`  
`                       "version": "0.5.0"}`  
`                 },`  
`        "scores": {`  
`                "774499188": {`  
`                           "wp10": {`  
`                                 "score": {`  
`                                       "prediction": "Stub",`  
                                        `"probability": {`
                                                   `"B": 0.03488477079112925,`
                                                   `"C": 0.06953258948284814,`
                                `"FA": 0.0025762575670963965,`
                                `"GA": 0.007911851615317388,`  
                                `"Start": 0.4106575723489943,`  
                                `"Stub": 0.4744369581946146`
 `                               }  `
                            }
                    }
                }
`            }  `  
`        }  `  
`}`  

__Article Quality Prediction Data__  

## Visualization 

![alt text](https://raw.githubusercontent.com/orbitse/data-512-a2/master/WikipediaBiasDataPlot.png)  
This visualization of the Wikipedia page view data was created with matplotlib. See the Jupyter Notebook file, hcds-a2-data-curation.ipynb, in this repository for the instructions on and how to create this visualization.

## Writeup 

Write a few paragraphs reflecting on what you have learned, what you found, what (if anything) surprised you about your findings, and/or what theories you have about why any biases might exist (if you find they exist). You can also include any questions this assignment raised for you about bias, Wikipedia, or machine learning. 
