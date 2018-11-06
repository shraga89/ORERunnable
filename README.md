### Welcome to the Ontobuilder Research Environment! ###


![about.gif](https://bitbucket.org/repo/n9GKe/images/3183918637-about.gif)


The Ontobuilder Research Environment (ORE) is designed to provide students and researchers in schema matching and related fields a jump-start in designing and running experiments. 

Development of ORE is managed by [Roee Shraga](sites.google.com/view/roee-shraga), Phd. student at [Technion IIT](http://www.technion.ac.il) under the academic guidance of [Avigdor Gal](http://ie.technion.ac.il/~avigal), Phd.

 To report bugs, request assistance or suggest additional features,

Roee by email:shraga89@campus.technion.ac.il

To gain access to the full code go to https://bitbucket.org/tomers77/ontobuilder-research-environment/, there you can find information regarding supported matchers, statistics, experiments and more.

## Installation: ##
# What you need ? #

In order to install and work the ORE you need the following components installed at your enviroment :

* MySQL Server ( for example: [MySQL Community Server](http://dev.mysql.com/downloads/mysql/))
* MySQL Managment Tool ( for example: [MySQL Workbench](https://dev.mysql.com/downloads/workbench/))
* Download all files from the git to your PC

# Installation Steps #

1. Download the datasets from [here](https://bitbucket.org/tomers77/ontobuilder-research-environment/downloads/dataset.zip) (remember where you saved them, you will need it).
2. Download a database named "schemamatching" from this [mysql db dump](https://bitbucket.org/tomers77/ontobuilder-research-environment/downloads/schemamatching_02_04_13.sql).

3. Perform post installation configuration:
Modify a text file named "ob_interface.properties" located in the "oreConfig" folder. The file should contain rows as follows:
dbmstype = 1
host = localhost
dbname = schemamatching
username = (a)
pwd = (b)
schemaPath = (c)
tmpPath - ./tmp/ 
(a)- Insert here your database user name. Mostly, the user name is "root", but some people may use a different user name. 
Note that the important thing is to name a user that has read/write privileges to the schema matching database.
(b)- Insert here the password of your user, as you defined in MySQL.
(c)- Insert the location of the dataset folder you downloaded in step 1.
Note that the format for windows based systems is: "c:\\foldername\\...\\foldername". Linux based systems have a different format.

Using MySQL to restore the "schemamatching" database:
Go to your MySQL server and create a database named " schemamatching" by using the command "CREATE DATABASE schemamatching;"
(before doing it, check that the database does not exist, buy using the command "SHOW DATABASES;").
After creating "schemamatching" database, (if you are working with the "basic" interface, make sure you select the database to use, with "USE schemamatching;") you will have to use the file downloaded at step 2 to restore it, by using the command "SOURCE file_2_url.sql;".
(if you failed to open the file (error2), try to remove the semi-colon in the end of execution line: instead "SOURCE file_2_url.sql;" try running "SOURCE file_2_url.sql") 
(if it still fails try adding a full path to the file, for example: source c:\folder\that\holds\your\backup.sql).
After running this command you should check all queries have been successfully committed.

#Check the Installation correctness#
Run the following cmd: "java -jar ORE.jar cmd ./res SimpleMatch 0 35 0 -f:0 -s:1"
(look for the results in the res folder)
