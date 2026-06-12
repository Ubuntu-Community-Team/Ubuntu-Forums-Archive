---
title: "ODBC Troubleshooting"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by suelip on 2007-08-08
I suspect my problem here is a lack of linux knowledge, so I'd really appreciate some general methods for checking the installation of my odbc driver. 

I am trying to set up an odbc connection on an ubuntu server i have ssh access to for a Java app to use to connect to a mysql 5 database. At present I am just trying to test the connection using isql

I initially installed the libmyodbc package using apt-get which installed version 3.51.11, which allowed me to connect with isql fine. However it appeared this version has some issues with stored procudures so I want to upgrade to 3.51.18.

I downloaded a package from mysqls site (mysql-connector-odbc-3.51.18-linux-x86-32bit.tar.gz, "arch" on the server gives i686 so I believe this is the correct one ) and tried to install this following their instructions (which was basically to copy the driver files to a suitable location and configure the odbc.ini and odbcinst.ini files) 

now i have the following situation...

-files called libmyodbc3.so and libmyodbc3S.so in /usr/lib/odbc

-the following entry in /etc/odbcinst.ini
[myodbc3]
Description     = MyODBC Driver
Driver          = /usr/lib/odbc/libmyodbc3.so
Driver64        = /usr/lib/odbc/libmyodbc3.so
Setup           = /usr/lib/odbc/libmyodbc3S.so
Setup64         = /usr/lib/odbc/libmyodbc3S.so
UsageCount      = 1
FileUsage       = 1

-the following entry in /etc/odbc.ini
[my_connection]
Driver          = myodbc3
DESCRIPTION     = connection
Password        = password
SERVER          = localhost
Database        = database
Option          = 3
UID             = root

- odbcinst -j gives the following (confirming that /etc/odbc... were the right places to define my driver and connection)
unixODBC 2.2.11
DRIVERS............: /etc/odbcinst.ini
SYSTEM DATA SOURCES: /etc/odbc.ini
USER DATA SOURCES..: /root/.odbc.ini

isql can still connect using the first odbc driver, but with the new connection i get...

root@none:~ # isql my_connection root password -v
[08S01][unixODBC][MySQL][ODBC 3.51 Driver]Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)
[ISQL]ERROR: Could not SQLConnect

I read a few forum entries about the mysql.sock just being in the wrong place, but doing a find for it returns no results. Should i be able to find it, or is it only created when a connection is made?

Any advice on how to start troubleshooting this problem would be much appreciated.

---

### Post by suelip on 2007-08-08
I have decided to use JDBC for this application.

---

