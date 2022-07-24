Calculate how much money is worth in a different country. Uses data from World
Bank.

Note: Works on python3.4 and above.

### Installation Instructions
1. Clone the source code

        git clone https://github.com/nigelbabu/pppconverter.git

2. Create a virtual environments and install the dependencies

        virtualenv -p python3 env
        source env/bin/activate
        pip install -r requirements.txt

3. Create the sqlite database by running the website.py file.

        ./manage.py runserver

4. Import the CSV into the sqlite database.

        ./manage.py importcsv -f data.csv

5. Run the site.

        ./manage.py runserver


### Updating the data
1. Download the CSV data from the [world bank portal][wb] and unzip the file.

3. Run the parsecsv.py script to create a file called parsed\_data.csv.

        ./manage.py parsecsv -f /path/to/file

4. Replace data.csv file with the newly created parsed\_data.csv file.

5. Import the new CSV into the sqlite database.

        ./manage.py importcsv -f data.csv

6. PROFITT!!



[wb]: http://data.worldbank.org/indicator/PA.NUS.PPP


## Updates by Omer:
1. Actual site on http://salaryconverter.nigelb.me
2. Downloaded new data 2021 and placed it in [2021_WorldBank_Data](2021_WorldBank_Data/API_PA.NUS.PRVT.PP_DS2_en_csv_v2_4354097.csv)
3. The main formula to convert salary from source country to destination country is $$ Salary in To-Country = { Salary in From-Country \over PPP(From-Country) } x PPP(To-Country) $$

4. Competing websites:
   1. https://www.chrislross.com/PPPConverter/
   2. https://www.numbeo.com/cost-of-living/compare_cities.jsp?country1=Pakistan&city1=Wah&country2=United+Arab+Emirates&city2=Dubai&amount=350%2C000.00&displayCurrency=PKR

5. Interesting Information Websites:
   1. https://www.worlddata.info/cost-of-living.php
   2. https://www.kaggle.com/code/mhajabri/salary-and-purchasing-power-parity/notebook
   
#### Errors:   
1. Removed errors by changing Flask version to `Flask==2.1.0` in requirements.txt
2. Removed error by replacing code line in script `/opt/anaconda3/envs/pppconverter/lib/python3.8/site-packages/flask_script/__init__.py` as follows
        - `#from flask._compat import text_type`
        - `from flask_script._compat import text_type`
3. Still webserver not working





