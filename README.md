# mysql-selfmanaged
homework


What cloud environment you decided to use
1) I decided to use GCP
How you set up your VM (what image you selected - imagine writing a brief tutorial to a new user - what would you include and how to quickly and easily set up a new VM) 

enabled http and https, used ubuntu found the approriate boot disk needed for the project and clicked create.

The commands you used to setup the OS image (how did you update the OS image? how did you install the mysql 

when working with a new environment it is important to make sure it is up to date. This can be done by running the following command
sudo apt-get update
to install mysql into the virtual machine 'mysql-server mysql-client'

What changes you needed to make in order to make the mysql instance available to external computers (config file? opening ports?) 

in order to make the instance available to external computers the following command was necessary:
sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf
once that code was used in the nano file the bind address had to be changed to 0.0.0.0 to allow external connections and then the program had to be restarted using:
sudo /etc/init.d/mysql restart
in addition in GCP a firewall rule was created to allow access for port 3306 which is sql default port



to upload the data: 
made sure the necessary packages were installed
!sudo apt-get install python3-dev default-libmysqlclient-dev
!pip install pymysql sqlalchemy
from sqlalchemy import create_engine
import pandas as pd
then connected to sql
df = pd.read_csv('https://healthdata.gov/resource/x7kq-cyv4.csv')
df
df.to_sql('table', con=db, if_exists='replace')

