---
title: "MySQL setup trouble"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-05-23
I installed LAMP on Ubuntu Desktop with this method:
```
sudo aptitude install php5 apache2 mysql-server
```

Now I'm configuring it so that MySQL can connect with the whole package by following this confusing guide.
[https://help.ubuntu.com/community/ApacheMySQLPHP#head-e8ed2e2ff6335c860b38aab7d029cdff0bc6215a](https://help.ubuntu.com/community/ApacheMySQLPHP#head-e8ed2e2ff6335c860b38aab7d029cdff0bc6215a)
I'm in the section where it says this:
> 
Edit PHP Configuration to Work With MYSQL (Ubuntu Dapper)

In Dapper Drake, "extension=mysql.so" and "extension=mysqli.so" are enabled in the php.ini file out-of-the-box. However, sometimes php is not looking for those files in the right directory. You have then to move your files or modify the php.ini configuration.:
First solution

locate the directory where the extension files are placed:

 locate mysql.so 

(change mysql.so in mysqli.so if you want to install the mysqli functions)

-then modify the php.ini file to indicate the right place for the extension directory:

$ gksudo "gedit /etc/php4/apache2/php.ini"

or if you are using php5

$ gksudo "gedit /etc/php5/apache2/php.ini"

Look for the 'extension_dir' property, and set it to the directory where you found the mysql(i).so file:

    *

      extension_dir= "/usr/lib/php5/20051025/"

Restart apache, and test if your mysql(i) functions are working. 


Here is where the confusion sets in.  I installed php5 acording to the aptitude.  When I cd /etc I see both php4 and php5 	:confused:
However I follow the instructions and do this
```
mike@sanka:/etc$ **locate mysql.so**
/usr/lib/perl5/auto/DBD/mysql/mysql.so
/usr/lib/python2.4/site-packages/_mysql.so
**/usr/lib/php4/20050606**/mysql.so
mike@sanka:/etc$
 
```
I get php4, I didn't install it I installed php5 why is LAMP brain ******* with me like this :(

---

### Post by az on 2007-05-23
You never installed the libapache2-mod-php5 package.


[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
"To install the default LAMP stack in Ubuntu 6.06 LTS (Dapper Drake)
If you did not use the LAMP installer option from the server cd but want to install those same packages without having to reinstall your operating system, use any method to install the following packages 

apache2 php5-mysql libapache2-mod-php5 mysql-server"

---

