# <u>**Arts Funding: A Matter of Principle**</u>
### An Ethical Data Analysis of Arts Council England National Lottery Award Distribution and Machine Learning

*Arts Funding: A Matter of Principle* examines patterns in public arts funding, distinguishes perceived inequalities from evidence of bias and evaluates the ethical implications of using machine learning to inform funding decisions.

It is essential stakeholders interpret data and implement machine learning models responsibly. The nature of the arts sector lies in its unpredictability. Cultural shifts across art forms and regional growth driven by collective movements can emerge spontaneously, often beyond the reach of historical data. 

This analysis brings a human perspective to the limitations of reductive statistics, examining how quantifiable patterns can flatten the complexity of creative practice by overlooking the social, cultural and regional contexts shaping artistic development.

## <u>**Business Requirements**</u>

A critical evaluation of the ethical implications to apply data analytics and machine learning onto public arts funding reinforces understanding of data responsibility, statistical interpretation, model limitations and accountable decision-making.

**Review data handling:** Evaluate the dataset's source, licensing uncertainty, data preparation decisions and minimisation.

**Interpret data responsibly:** Examine regional and disciplinary differences in ACE National Lottery Project awards, distinguishing statistical disparities from evidence of bias.

**Evaluate model reliability:** Assess the Random Forest classification model using its existing performance metrics and determine whether its predictions are suitable for informing funding decisions.

**Identify risks of misrepresentation:** Consider how regional differences, disciplinary representation, class imbalance and missing contextual information may influence visualisations and model predictions.

**Consider human oversight:** Evaluate why machine learning predictions should not replace contextual assessment, professional judgement or accountable decision-making in arts funding.

**Communicate ethical findings:** Present the analysis, limitations and recommendations to non-technical stakeholders.

## <u>**Dataset**</u>

**Dataset used**: (1) National Lottery Project Grants - List of Awards in Year 2023-2024 and (2) National Lottery Project Grants - List of Awards in Year 2025-2026

**Source**: Arts Council – Project Grants Data

**Dataset link**: https://www.artscouncil.org.uk/ProjectGrants/project-grants-data

**Format**: EXCEL sheets exported as CSV files 

**Columns**: Recipient, activity name, award amount, decision date, decision month, decision quarter, ACE Area, local authority, main discipline and time-Limited Priority. 

## <u>**Data Licensing**</u> 

[Arts Council England – Project Grants Data](https://www.artscouncil.org.uk/ProjectGrants/project-grants-data) was downloaded from the official website. The [Open Government Licence v3.0](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/) allows data covered by the licence to be reused and adapted, provided the source is credited and the licence conditions are followed.

The third-party website [DOGE UK – Arts Council England Grant Data](https://doge-uk.com/funding/arts-council-england-all-grants/) lists the National Lottery Project Grants data under this licence. However, this could not be independently confirmed through ACE's own website. A search of ACE's listings [data.gov.uk](https://www.data.gov.uk/search?page=1&q=Catalogues&query=Catalogues) found other ACE datasets listed under the OGL, but not the specific dataset used in this project.. 

In comparison, the [National Lottery Heritage Funds](https://www.heritagefund.org.uk/about/insight/open-data) explicitly states that its grant data is published under the OGL and available for reuse. It identifies policymakers, researchers, journalists, heritage organisations, potential applicants and the public as intended audiences. This illustrates how clear licensing information can support access to public funding data, although the Heritage Fund's arrangements do not confirm the licence applicable to ACE's data.

The next step is to contact ACE to confirm the applicable licence terms and review whether the dataset should remain publicly available in the repository.

## <u>**Freedom of Information and Transparency**</u>

The [Information Commissioner's Office (ICO)](https://ico.org.uk/for-organisations/foi/what-is-the-foi-act-and-are-we-covered/) explains that the Freedom of Information Act 2000 gives the public the right to request recorded information held by public authorities. It also requires public authorities to publish certain information about their activities. This supports transparency and public accountability.

In the context of arts funding, access to information can help researchers and the public better understand how public funding is distributed. However, published grant data alone cannot explain every funding decision or establish whether inequalities are evidence of bias. Further information, such as assessment criteria and application success rates, may be needed to understand the wider context.

## <u>**Disclaimer**</u>

*Arts Council England Awards Painted by Numbers* was produced for educational purposes as part of the Code Institute Advanced Data Analytics, Visualisation and Machine Learning Summative Assessment 2. The project simulates a real-world data analysis and fulfils the requirements of the Data Analytics with AI Skills Diploma.

*Arts Funding: A Matter of Principle* also informs the ethical considerations for Summative Assessment 3. This project reflects on the responsible use of public funding data, transparency, data protection and the limitations of machine learning in arts funding decisions.

This is an independent educational analysis and is not endorsed by Arts Council England (ACE). The licence applicable to the dataset could not be independently verified. 

## <u>**Hypothesis**</u>

The initial hypothesis motivating this project stems from a familiar question within the arts sector: *Are National Lottery Project Grants fairly distributed across regions, artforms and funding streams?*

This project is underpinned by the personal assumption that funding may not be distributed equally across the cultural sector, reflecting concerns many artists face when navigating public funding systems.

The following research questions apply descriptive and diagnostic analysis to examine funding patterns and investigate potential factors associated with differences in award amounts.

1. *Are ACE National Lottery Project Grants unevenly distributed across geographic areas?* The hypothesis is that award amounts and grant counts differ across ACE areas. This is investigated through a bivariate analysis in the EDA notebook, alongside Welch’s ANOVA to test whether the differences in mean award amounts between regions are statistically significant.

2. *Do certain main diciplines receive more or less funding than others?* Descriptive analysis compares award amounts across main disciplines to identify differences in funding distribution. Domain knowledge is then applied to interpret these patterns in the context of the cultural sector and consider potential explanations for differences in funding. 

3. *Can a machine-learning model predict award amount tiers with reasonable accuracy using categorical features?* Model accuracy is evaluated to assess how effectively machine learning can automate the prediction of award amount tiers using categorical features. Feature importance is also examined to identify which attributes contribute most to the model's predictions and reveal potential patterns in award amounts.

## <u>**Project Plan**</u>

An end-to-end analytical workflow moves from raw data to an insightful dashboard, presenting discoveries from EDA alongside a simple machine-learning model designed to identify funding patterns.

**Data Collection** - Two publicly accessible ACE National Lottery Project Grants datasets (2023–2024 and 2025–2026) are loaded from the Arts Council website for this project.

**Extract, Transform, Load (ETL)** - Data integrity is ensured prior to analysis by standardising column names and inspecting and addressing missing, unique or duplicate records. Reviewing data types ensures numerical, date-time and categorical columns are compatible with plotting in the EDA notebook. 

The final step joins the two datasets, adds a year column and removes columns containing potentially sensitive information to support responsible data handling. The resulting DataFrame is saved in the clean data folder.

**Exploratory Data Analysis (EDA)** - Award amount patterns are explored across ACE areas, main disciplines and funding streams using Pandas, NumPy, Matplotlib and Seaborn to visualise distributions and differences through boxplots, scatterplots, histograms and bar charts. 

Statistical techniques, including descriptive statistics and Welch’s ANOVA, complement these visualisations by summarising award distributions and testing whether mean award amounts differ significantly between ACE regions.

**Feature Engineering** - The clean, joined DataFrame undergoes further preparation for machine learning. Award amounts are grouped into funding tiers to create the target variable for multiclass classification. Columns that could cause data leakage and affect model quality are dropped, and the model DataFrame is saved.

**Machine‑Learning Model** - A Random Forest classification model is trained to predict award amount tiers (Low, Medium and High), using an 80/20 train-test split and stratified five-fold cross-validation. 

Model performance is evaluated using test accuracy, macro F1-score, precision, recall and a confusion matrix comparing actual and predicted tiers. Feature importance is then assessed to identify which attributes contribute most to the model's predictions.

**Dashboard Creation** - A Tableau dashboard frames visualisations and paints the numbers of year-on-year award amounts across ACE areas, main disciplines and funding streams. The interactive dashboard explores the research hypotheses, connecting the findings to reveal patterns in cultural funding. The dashboard also presents the multiclass machine-learning model's accuracy to assess how effectively it predicts award amount tiers and whether machine learning can identify meaningful patterns in creative funding.

## <u>**Analysis Techniques Used**</u>

**Descriptive Statistics** - Numerical statistics are reviewed to identify means, modes and percentiles, and to detect anomalies in columns that may require further inspection to ensure data quality and improve model performance. 

**Univariate Analysis** - Histograms, boxplots and bar charts are used to visualise the distribution of awards across numerical and categorical variables, exploring differences between geographic areas and whether certain main disciplines receive more or less funding.

**Bivariate Analysis** - Award amounts are compared across pairs of variables to examine differences in funding between categories and identify patterns in how much recipients receive.

**Outlier Inspection** - Anomalies identified in descriptive statistics are inspected to verify data quality and determine how they should be handled for the machine-learning model.

**Hypothesis Testing** - Welch’s ANOVA is applied to test whether mean award amounts differ significantly across ACE regions. The p-value is used to assess statistical significance and determine whether there is sufficient evidence to reject the null hypothesis.

## <u>**Hypothesis Validation**</u>

As the project developed, conversations with local artists challenged the original hypothesis, grounding the analysis in lived experience rather than quantitative features alone. These discussions highlighted how funding patterns may reflect the cultural ecosystems artists build around themselves.

For example, Stourbridge’s glassmaking heritage has shaped a distinct creative identity in the Black Country, whilst Birmingham’s heavy-metal legacy has produced generations of musicians. These local histories help explain how clusters of artistic activity emerge.

Above all, the project highlighted that data, whilst insightful, is not neutral. Patterns can be interpreted differently depending on the storyteller’s perspective, agenda or assumptions. Relying solely on statistical outputs or machine-learning predictions risked reinforcing bias by allowing initial assumptions to shape the narrative rather than the evidence.

**Are ACE National Lottery Project Grants unevenly distributed across geographic areas?**

**Result:** Supported

**Summary:** Welch’s ANOVA rejected the null hypothesis that mean award amounts are equal across ACE regions, providing statistical evidence of differences between regional averages.

The visual analysis also supports this finding, showing variation in award amounts despite positively skewed distributions.

However, these differences do not necessarily indicate unfair funding distribution. Further investigation considered potential explanations, including ACE’s strategic allocation of funding to areas in need and London’s higher population density, which may contribute to differences in the number of awards.

**Do certain main diciplines receive more or less funding than others?**

**Result:** Supported

**Summary:** Boxplots and barcharts show variation in award amounts across main disciplines. Theatre, Music and Dance appear to have higher award amounts, whilst Digital Arts appears to have lower award amounts in the dataset.

Based on domain knowledge of the arts sector, these differences may reflect the varied cost structures of creative practice, from large-scale theatre productions to small-scale independent artistic development. 

Nonetheless, this remains a potential explanation rather than a conclusion established by the visualisation and further investigation would be needed to establish the reasons for these differences.


**Can a machine-learning model predict award amount tiers with reasonable accuracy using categorical features?**

**Result:** Unsupported

**Summary:** The Random Forest classifier achieved a test accuracy of 39.60% and a macro F1-score of 39.56%. The confusion matrix showed that the model correctly classified 41.4% of Low-tier projects, 40.2% of Medium-tier projects and 37.2% of High-tier projects. These results indicate limited predictive performance, with substantial misclassification across all three award tiers.

Main discipline and ACE area were identified as influential predictors within the model. However, these rankings do not establish causation or explain individual funding decisions.

The results do not support using this model to reliably predict award amount tiers. Instead, they demonstrate the limitations of predicting complex cultural funding outcomes using a restricted set of categorical features.

## <u>Dashboard Overview</u>

A Tableau dashboard was designed to translate exploratory data analysis and machine-learning insights into accessible visual insights for arts-sector stakeholders. The dashboard explores the geographical distribution of ACE National Lottery Project Grants, compares award amounts across artistic disciplines and presents model evaluation metrics.

Together, these visualisations examine potential patterns in public arts funding and provide an evidence base for further discussion about its distribution.

#### **Dashboard Features**

- Funding analysis between geographic and artform.
- Model performance evaluation metrics. 
- KPI cards to highlight numeric summaries.
- Interactive filtering and slicing between years, regions and funding streams.
- Tooltips to view average and median award sizes. 
- Simple UX design to optimise visual clarity. 

**Live Dashboard Link:**
https://public.tableau.com/app/profile/viktoria.tchibor/viz/ArtsCouncilEnglandAwardsPaintedByNumbers

#### **Dashboard Pages**

**Page 1 — Does where you are influence how much funding you receive?** Explore how ACE National Lottery Project Grants are distributed across geographic areas, highlighting regional differences in award numbers and amounts.

![Arts Council England Funding Dashboard](images/tableau_sheets/1_landscape_of_arts_funding.jpeg)

**Page 2 — What does funding patterns look like across artforms?** Compare award amounts across main artistic disciplines and funding streams to identify differences in funding levels and variation.

![Arts Council England Funding Dashboard](images/tableau_sheets/2_inside_the_funding_mix.jpeg)

**Page 3 — Can Machine Learning make sense of creative funding?** Random Forest model evaluation metrics are displayed to determine whether funding patterns can be reliably made using categorical features.

![Arts Council England Funding Dashboard](images/tableau_sheets/3_ml_model_performance.jpeg)


## <u>Development Roadmap</u> 

**ETL** intially data types are converted in the notebook. However, missing values identified at the beginning were not handled prior to converting categorical columns into category which meant the time-limited piority column failed to convert from its default string data type. Thus, I took a step back to ensure the values contained in the rows are cleaned. 

Data-time columns took a moment to adjust accordingly due to a misunderstanding with built-in Copilot on the task to modify code. Stack Overflow informed me on the difference between <code>normalize()</code> and <code>.dt.date</code> usage.

## <u>**Project Management**</u>

A project board was created and reviewed daily to ensure assessment criteria was met in the allocated time-frame. Issues were created including user stories outlining who, what and the benefits for each step. Additional, subissues are included to monitor progress at each stage of the project.

**Project Board Link:** https://github.com/users/vik4t11/projects/7

![ACE Project Board](images/project_board/ace_project_board.jpeg)

## <u>**Technologies Used**</u>

#### **Analysis Tools**

- *Python:* Programming language used for coding ETL, EDA, Feature Engineering and Machine Learning Model notebooks.
- *Jupyter Notebooks:* documentation tool to run and explain code cells.
- *Pandas:* data manipulation, cleaning, analysis and DataFrames.
- *NumPy:* numerical computing, arrays and mathematical operations.
- *Matplotlib:* creating charts and data visualisations.
- *Seaborn:* statistical visualisations built on Matplotlib.
- *Scikit-learn:* machine learning, preprocessing, model training and evaluation.
- *SciPy:* scientific computing, statistics, optimisation and advanced mathematics.

#### **Dashboarding**

- *Tableau Public:* used to design an interactive dashboard for non-technical stakeholders to explore insights on National Lottery Project Grants. 

#### **Version Control**

- *Git:* version control tool to commit changes made on the project.
- *GitHub:* repository host and project board management. 

## <u>**Improvements**</u>

The Random Forest classification model was selected to identify trends in the dataset. The models performance was limited but does not eliminate the possibility of engineering a Decision Tree model to compare results. 

Once a compatible model is selected and trained a Streamlit app that allows stakeholders to select a different combination of features using a drop down menu could be produced as a product for independent descriptive analytics to identify patterns in past data.

A map to plot the award distributions across ACE regions would require an additional DataFrame to define the borders for visualisation on Tableau.

## <u>**AI Usage**</u>

ETL and EDA is predominantly produced using the sources included in the credits section with in-built Copilot modification applied to improve UX design for visualisations and adding comments to code. 

In the ML Model notebook Chat GPT and Copilot support the majority of the workflow to write code and interpret results. This challenged my original intention to reduce scraping the internet from websites such as Stack Overflow who are impacted by the lack of credit to engineers who wrote original code. 

With this being said, due to the assessment criteria requirement AI collaboration is clearly demonstrated to speed up the process, which would reduce timely costs for organisations and help them reach their business requirements much quicker with advanced AI accessibility.

## <u>**Ethical Considerations**</u>

Random Forest and other tree‑based models used in this project are topic‑agnostic: they treat creative‑sector data the same way they would treat any other domain, meaning the interpretation of their outputs depends heavily on the analyst’s narrative lens. Without human context, these models could unintentionally reinforce bias‑driven interpretations.

To avoid this, I combined quantitative analysis with cultural context and human insight, recognising that creative practice cannot be reduced to topic‑agnostic modelling. This approach ensures the project remains legally compliant, ethically grounded, and sensitive to the societal realities of the arts sector.

This project also acknowledges the ethical challenge of applying machine‑learning models to creative practice. Artistic work is nuanced and culturally embedded, and reducing it to categorical features risks oversimplification.

## <u>**Credits**</u> 

**Data Licence**

*Heritage fund open data comparison* - https://www.heritagefund.org.uk/about/insight/open-data

*Open Government Licence* - https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/

*ACE Datasets Open Government License third-party claim* - https://doge-uk.com/funding/arts-council-england-all-grants/

*National Data Library* - https://www.data.gov.uk/search

**Other**

*Freedom of Information Act 2000* - https://ico.org.uk/for-organisations/foi/what-is-the-foi-act-and-are-we-covered/

*Ethical consideration* - https://www.channel4.com/programmes/molly-vs-the-machines

*Critical use of generative AI* - https://subjectguides.york.ac.uk/critical/ai

## <u>**Acknowledgements**</u>

I acknowledge and appreciate the use of ChatGPT, Gemini and GitHub Copilot throughout this project. 

Thank you to Mike for encouraging me to join Code Institute and Laura for supporting me to secure a place on the course. Thank you to my tutor Emma for teaching me there is, in fact, method in the madness. 

I'm grateful for the wellbeing support from my friend Patsy and the Ivkos for accommodating me throughout the learning process. # Arts_Funding_Ethical_Analysis
