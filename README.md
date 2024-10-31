# Course Project: Part 1 - Common Analysis
## Impact of Wildfires on the city of Vancouver, WA

## Project Goal
The primary goal of this project is to analyze the impacts of wildfires on the city of Vancouver, WA, with a specific focus on estimating and understanding the effects of wildfire smoke on public health and air quality over the last 60 years, from 1961 to 2021. ​This analysis aims to produce annual estimates of wildfire smoke impacts based on data from wildland fire occurrences within a 650-mile radius of Vancouver.​ By leveraging historical wildfire data, Air Quality Index (AQI) metrics, and predictive modeling techniques, the project seeks to accomplish the following key objectives:
- Estimate Annual Smoke Impact: Create a method for estimating the annual impact of wildfire smoke on Vancouver, WA, considering factors such as the intensity and proximity of wildfires. This estimation will serve as a quantitative representation of the smoke's influence on the city's environment and public health.
- Visualize Historical Trends: Produce visual representations (histograms and time series graphs) of key metrics related to wildfires, including the distribution of wildfire occurrences by distance from the city, total acres burned per year, and comparisons between estimated smoke impacts and AQI values.
- Inform Policy Decisions: Provide insights and data to inform city managers, policymakers, and other civic institutions in their planning and decision-making processes concerning wildfire management, public health interventions, and air quality improvement strategies.
- Forecast Future Impacts: Develop a predictive model that forecasts smoke estimates for the next 25 years (2025-2050), enabling Vancouver to prepare for potential future wildfire smoke impacts. This forecast will include confidence intervals to represent the uncertainty associated with smoke estimates.

Through this project, the analysis aims not only to quantify the historical impacts of wildfires in Vancouver, WA but also to contribute to the broader understanding of how wildfire smoke affects urban environments, ultimately aiding in the development of more effective mitigation strategies.

This project follows to the best practices for open scientific research as mentioned in chapters "Assessing Reproducibility" and "The Basic Reproducible Workflow Template" of ["The Practice of Reproducible Research: Case Studies and Lessons from the Data-Intensive Sciences"](https://www.ucpress.edu/books/the-practice-of-reproducible-research/paper) publication, ensuring transparency and reproducibility throughout the process.

## Licenses
### Datasets used
- **USGS Wildland Fire Combined Dataset**: This dataset serves as the primary source of data for the project and contains comprehensive wildfire data. The dataset was downloaded from this [link](https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81) as part of the 'GeoJSON Files.zip' file. It is cited by Welty, J.L., and Jeffries, M.I. (2021). Combined wildland fire datasets for the United States and certain territories, 1800s-Present: U.S. Geological Survey data release. [doi](https://doi.org/10.5066/P9ZXGFY3). While the specific usage policy for this dataset is not explicitly stated, it is assumed to be safe to use.
- **Air Quality Index Data**: Air Quality Data was needed to evaluate the performance of the smoke estimate created. This data was requested from the US Environmental Protection Agency (EPA) Air Quality Service (AQS) API. This is a historical API and does not provide real-time air quality data. The [documentation](https://aqs.epa.gov/aqsweb/documents/data_api.html) for the API provides definitions of the different call parameter and examples of the various calls that can be made to the API. The US EPA was created in the early 1970's. The EPA reports that they only started broad based monitoring with standardized quality assurance procedures in the 1980's. Many counties will have data starting somewhere between 1983 and 1988. However, some counties still do not have any air quality monitoring stations. The API helps resolve this by providing calls to search for monitoring stations and data using either station ids, or a county designation or a geographic bounding box. Some additional information on the Air Quality System can be found in the [EPA FAQ on the system](https://www.epa.gov/outdoor-air-quality-data/frequent-questions-about-airdata). The AQS API is publicly accessible and provides access to ambient air sample data collected by various pollution control agencies. Users are expected to be familiar with the terms of service that govern the use of the API. These [terms](https://aqs.epa.gov/aqsweb/documents/data_api.html#terms) outline acceptable usage practices and any restrictions on data access and storage

### Repository
The repository is licensed under the MIT License, and it permits users to freely use, modify, and distribute the code, provided that the original copyright notice and permission notice are included in all copies or substantial portions of the software.

A few snippets used in the script is developed by Dr. David W. McDonald for use in DATA 512, a course in the UW MS Data Science degree program. This code is provided under the [Creative Commons](https://creativecommons.org) [CC-BY license](https://creativecommons.org/licenses/by/4.0/). Revision 1.1 - August 16, 2024

## Workflow

The code was executed on MacBook Pro. Before running this project, ensure that the required mentioned at the top of each of the scripts are installed. Additionally, please create the necessary folders and adjust the file paths as required for your environment.

Due to space limitations, I could not have the data folder in the repository. Access the data from [here](https://drive.google.com/drive/folders/1yR7RkC28EGOouKa2W3QquWPzH_bZP3I_?usp=sharing).
    - The intermediate data files can be accessed [here](https://drive.google.com/drive/folders/1ourdQkuUAiW_qeXRpL0K_y6oiG-ZwQgX?usp=share_link). 
        - [wildfire_dataset_with_distance.csv](https://drive.google.com/drive/folders/1ourdQkuUAiW_qeXRpL0K_y6oiG-ZwQgX?usp=share_link): All the valid 118465 wildfire instances close to Vancouver, WA are mentioned here. 
        - [wildfire_dataset_with_distance_cutoff.csv](https://drive.google.com/file/d/1Mlcswoag46e3cPsug-51mddHWsc5nIOS/view?usp=sharing): All the 68394 filtered wildfire instances are mentioned here (according to the assignement specifications). 
        - [wildfire_dataset_with_distance_and_smoke_estimate_by_date.csv](https://drive.google.com/file/d/1Mlcswoag46e3cPsug-51mddHWsc5nIOS/view?usp=sharing) and [wildfire_dataset_with_distance_and_smoke_estimate_by_date.csv](https://drive.google.com/file/d/1Mlcswoag46e3cPsug-51mddHWsc5nIOS/view?usp=sharing): Filtered Wildfire datasets across all the dates and grouped by year are available here.
        - [aqi_data_grouped_by_date.csv)]([wildfire_dataset_with_distance_and_smoke_estimate_by_date.csv]()) and [aqi_data_grouped_by_year.csv]([wildfire_dataset_with_distance_and_smoke_estimate_by_date.csv]()): AQI data grouped by dates and years are available here.

To run this project, execute the notebooks in the folder [code](https://github.com/parvatijay2901/data-512-project-part1/tree/main/code).

- [step01_data_acquisition_fire_data.ipynb](https://github.com/parvatijay2901/data-512-project-part1/blob/main/code/step01_data_acquisition_fire_data.ipynb): We primarily obtain the wccess to the historical data of wildfires, and compute the average distance between the city assigned to me and the fire perimeter as this is required to obtain the smoke estimate. We will talk more about this estimate in the next notebook.

- [step02_create_fire_smoke_estimates.ipynb](https://github.com/parvatijay2901/data-512-project-part1/blob/main/code/step02_create_fire_smoke_estimates.ipynb): ​This notebook analyzes the impact of wildfire smoke on Vancouver, WA, focusing on data from the last 60 years.​ We begin by loading the wildfire dataset (extracted in the previous step) while filtering for fires that occurred during the fire season (May to October). Through exploratory data analysis, we define a smoke estimate based on fire size, type, and distance from the city, subsequently calculating and scaling these estimates. We finally aggregate and visualize yearly wildfire occurrences and smoke estimates and save the generated dataset for further reference.

- [step03_data_acquisition_aqi.ipynb](https://github.com/parvatijay2901/data-512-project-part1/blob/main/code/step03_data_acquisition_aqi.ipynb): We will request data from the US Environmental Protection Agency (EPA) Air Quality Service (AQS) API.

- [step04_predictive_modeling_and_smoke_analysis.ipynb](https://github.com/parvatijay2901/data-512-project-part1/blob/main/code/step04_predictive_modeling_and_smoke_analysis.ipynb): We use an ARIMA model to forcast smoke estimates for the next 25 years in this notebook. We also see the relationship betweem AQI and smoke estimates and list down the observations. Additionally, we also visualizes fire frequency, intensity, and total acres burned within 1800 miles of Vancouver, underscoring the need for further model refinement and alternative metrics for a more comprehensive assessment of wildfire impacts.

## Known Issues and Special Considerations
1. Data Quality and Limitations
    - The datasets used for analysis may not capture all relevant wildfires due to reporting inconsistencies or gaps in historical records. 
    - The smoke estimates generated in this analysis rely on simplified assumptions regarding fire size, type, and distance from the city. These estimates do not account for numerous factors that influence smoke distribution, including wind direction, atmospheric conditions, and fire duration.

2. Modeling Assumptions
    - The model’s assumptions regarding fire type and size impact the smoke estimate significantly. While various fire types have distinct impacts, the use of weighted values may oversimplify their effects, neglecting nuances in burn behavior and emissions.
    - The ARIMA model necessitates that the time series data be stationary. While differencing was applied to achieve stationarity, reliance on this technique can variability lose inherent trends, which may result in model performance issues, especially in long-term predictions.

3. Temporal and Spatial Considerations
    - The analysis does not account for temporal factors such as seasonal variations in fire occurrence and weather patterns, which could influence air quality and smoke dispersion. The historical period of analysis may not accurately reflect future trends, especially in the context of climate change.
    - The study focuses on Vancouver, WA, but wildfires that occur in distant regions can also impact air quality, albeit to a lesser degree. The model does not account for the cumulative effects of multiple wildfires occurring beyond the specified cutoff distance of 650 miles.

4. Correlation with AQI
    - The weak Spearman correlation between smoke estimates and AQI values suggests that other contributing factors may also play significant roles in determining air quality. 

5. Forecasting Limitations
    - Projections extending 25 years into the future entail substantial uncertainties. Changes in land use, fire management practices, climate policy, and wildfire behavior due to climate change can significantly affect future smoke estimates.

Other inferences are documented in the scripts and in the [project report](https://github.com/parvatijay2901/data-512-project-part1/blob/main/project_report.pdf).

## Research Practices

The project followed the best practices outlined in “The Practice of Reproducible Research” to ensure transparency and ease of replication:

- The project maintained a hierarchical structure, separating scripts and data, into distinct folders (`scripts/` and `data/`) for better organization. 
- Dependencies were clearly listed on top of each scripts. This helps in easy replication of the environment.
- The workflow was automated using Jupyter notebooks. This helps in seamless re-execution of the analysis.
- I avoided hard coding paths. This made the project more simple and better adaptable for different environments.
- The scripts and functions are clearly separated to provide anyone looking into the project to have better clarity.
- Finally, the README provided clear instructions for running the project and understanding its objectives.

The project could be improved by incorporating best practices such as using logging, maintaining a .gitignore file, and applying additional workflow improvements. However, it serves its purpose for the current scope of analysis to a good extent.

## Additional Notes

ChatGPT was used in this assignment as a grammar and vocabulary checker, as well as to rephrase content that I wrote myself.