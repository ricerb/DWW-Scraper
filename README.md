# DWW-Scraper Quick Guide

This is a brief explanation of how the drinking water watch (DWW) scraper script works. The application is currently split up into three jupyter notebooks to be run in the following order. They scrape lab samples stored in HTML tables on subpages captured in the DWW non-coliform samples search. The samples are stored in a bunch of small .pkl files, then stitched together into one large dataframe.

### 1. DWW_Scraper.ipynb:

This is the main web scraping script. It takes a long time to run (i.e. a few days running continuously to get through 5 years of statewide data). This opens up the URL of the DWW non-coliform samples search results page, clicks on all of the links on the page, then stores data from the tables on each of the lab samples pages in a pandas dataframe. It iterates through each county and year individually to break up the scraping into small chunks, so you don't lose all your progress when it breaks. Each of these chunks is stored in .pkl files.

To adapt this to another state's DWW site, I think you will just need to change the url within the run_script() function and create an appropriate list of counties.

### 2. Load pickles into dww dataframe.ipynb

The .pkl files from the previous step are stitched together into one large .pkl file.

### 3. DWW Data Cleaning.ipynb:

This removes extra characters from the data and saves it as a .csv file. Concentration measure and units are split into two separate columns.
