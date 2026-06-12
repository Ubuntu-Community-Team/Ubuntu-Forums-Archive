---
title: "[SOLVED] Upgraded from 6.1 to 7.04 and now can not connect to MySQL"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by stoshb on 2007-12-14
I just upgraded from 6.10 to 7.04.  In the process I managed to kill my php app that accessed the MySQL database.  

Now I keep getting 

Call to undefined function: mysql_connect() 

from my php programs.  

I have searched all over and see items about changing the extension_dir directive in php.ini.  I have tried a number of changes with that.

I feel that my php4 configuration may have been deleted and then php5 installed wrong.  I keep trying to reinstall php4 but get messages about this no longer being supported.  When I try to get phpinfo my sever gives me information about php4.  However, I have all sorts of libraries for php5.

I want this to be a very vanila system but am getting no where fast.  

Suggestions appreciated.

---

### Post by llamakc on 2007-12-14
Is MySQL running? Do you have libapache2-mod-auth-mysql installed?

---

### Post by stoshb on 2007-12-14
MySQL is running and I can get to it from the command line.  Just can not get to it from apache.

Get
stan@Dilbert:/etc/php5/apache2$ locate ibapache2-mod-auth-mysql
/var/cache/apt/archives/libapache2-mod-auth-mysql_4.3.9-2.1ubuntu2_i386.deb
/var/lib/dpkg/info/libapache2-mod-auth-mysql.prerm
/var/lib/dpkg/info/libapache2-mod-auth-mysql.list
/var/lib/dpkg/info/libapache2-mod-auth-mysql.conffiles
/var/lib/dpkg/info/libapache2-mod-auth-mysql.md5sums
/usr/share/doc/libapache2-mod-auth-mysql
/usr/share/doc/libapache2-mod-auth-mysql/changelog.Debian.gz
/usr/share/doc/libapache2-mod-auth-mysql/copyright
/usr/share/doc/libapache2-mod-auth-mysql/USAGE.gz
/usr/share/doc/libapache2-mod-auth-mysql/DIRECTIVES.gz
stan@Dilbert:/etc/php5/apache2$ 

so I guess that package is installed.  Correct me if this is not the answer to your question.

Thanks

---

### Post by dwblas on 2007-12-14
> Call to undefined function: mysql_connect()What programming language are you using and do you need/have a MySQL wrapper for that language installed.

---

### Post by stoshb on 2007-12-14
Thats what comes from php when running any php script that attempts to connect to MySQL.  Also can not run the PhpMyAdmin script as it says:

phpMyAdmin - Error

Cannot load mysql extension. Please check your PHP configuration. - Documentation

Best I can see all is OK, but the is obviously not the case

---

