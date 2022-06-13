# information_component_of_monetary_shocks
This repository contains the follow-up code for the Capstone Project 2021 "Analysing Central Bank of Russia Communication Impact on Monetary Policy Effectiveness With NLP", written under supervisor Mariam Mamedli.

## Data collection and processing for informational component
Notebooks:
* [getting_press_release_data.ipynb](https://github.com/tssorokina/information_component_of_monetary_shocks/blob/main/getting_press_release_data.ipynb) collects press release data from Bank of Russia Web-Page;
* [getting_news_data.ipynb](https://github.com/tssorokina/information_component_of_monetary_shocks/blob/main/getting_news_data.ipynb) collects relevant news from rbc.ru and lents.ru sites. Also contains filter for the news;


Collected data:
* [cbr_previews.xlsx](https://github.com/tssorokina/information_component_of_monetary_shocks/blob/main/cbr_previews.xlsx) dataset with CBR previews;
* [only_rbc_news_upd16042022.xlsx](https://github.com/tssorokina/information_component_of_monetary_shocks/blob/main/only_rbc_news_upd16042022.xlsx) dataset with all news from "rbc finance" and "rbc economics", 4 days before press release time, classified by respective dates of press releases (has the column with indices of corresponding press release from the file [cbr_previews.xlsx](https://github.com/tssorokina/information_component_of_monetary_shocks/blob/main/cbr_previews.xlsx));

### Stage 1: Text Embedding
Notebooks:
* [stage_1_text_embedding.ipynb](https://github.com/tssorokina/information_component_of_monetary_shocks/blob/main/stage_1_text_embedding.ipynb) 

Files:
* [cb_1306022_sbert.pt](https://github.com/tssorokina/information_component_of_monetary_shocks/blob/main/cb_1306022_sbert.pt) CBR press release embeddings (SBERT model);
* [news_rbc_13062022_sbert.pt](https://github.com/tssorokina/information_component_of_monetary_shocks/blob/main/news_rbc_13062022_sbert.pt) news embeddings, averaged over each press release date  (SBERT model);
* [cb_1306022_deeppavlov.pt](https://github.com/tssorokina/information_component_of_monetary_shocks/blob/main/cb_1306022_deeppavlov.pt) CBR press release embeddings (DeepPavlov ruberta model);
* [news_rbc_13062022_deeppavlov.pt](https://github.com/tssorokina/information_component_of_monetary_shocks/blob/main/news_rbc_13062022_deeppavlov.pt) news embeddings, averaged over each press release date (DeepPavlov ruberta model)


### SVAR model
Folder [variables_svar_model](https://github.com/tssorokina/information_component_of_monetary_shocks/tree/main/variables_svar_model) contains variables for SVAR model. The model, constructed with the use of these variables, replicates the specifications of closed economy and small open economy from Bannikova, Pestova (2021).
The links to data:

Variable | Units of measurement | Notation | Link to the data source
--- | --- | --- | --- 
Key rate | % | Policy Rate | [Bank of Russia Web-Page](https://www.cbr.ru/eng/hd_base/KeyRate/)
Industrial production index | 2010=100 | IP | [Russian Federal State Statistics Service](https://rosstat.gov.ru/compendium/document/50802)
Consumer Price Index | 2010=100 | CPI | [Russian Federal State Statistics Service](https://rosstat.gov.ru/compendium/document/50802)
Credit spread IFX-CBONDS G-spread | percentage point | Credit Spread | [Independent database of finansial data "Invest Funds"](https://investfunds.ru/indexes/22185/)
Nominal effective exchange rate | 2010=100 | NEER | [Bank for International Settlements (BIS) Web-Page](https://stats.bis.org/statx/srs/tseries/EER/M.N.B.RU?t=i1&p=201909&m=B&c=&o=w:201902.202002,s:line)
Global volatility index | no measure | Index VIX | [Chicago Board Options Exchange Web-Page](https://www.cboe.com/tradable_products/vix/vix_historical_data/)
