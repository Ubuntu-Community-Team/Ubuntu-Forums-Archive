---
title: "Newbie cant install phpmyadmin"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by andre_n_costa on 2007-06-16
hello all,

ive just installed ubuntu 6.06 lts, and and installing a lamp server from scratch. apache. php and mysql are installed and working just fine. 

but when i try to install phpmyadmin and got this error:

root@server:/home/andre# apt-get install phpmyadmin
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package phpmyadmin

i also tried sudo apt-get install phpmyadmin on my user account but did not work either!

what could be the problem here?

thanks in advance for you help


PS: these are the packages installed:
root@server:/home/andrenicolai# dpkg -l | grep php
ii  libapache2-mod-php5          5.1.2-1ubuntu3.8          server-side, HTML-embedded scripting languag
ii  php5                         5.1.2-1ubuntu3.8          server-side, HTML-embedded scripting languag
ii  php5-common                  5.1.2-1ubuntu3.8          Common files for packages built from the php
ii  php5-mysql                   5.1.2-1ubuntu3.8          MySQL module for php5
ii  php5-mysqli                  5.1.2-1ubuntu3.8          MySQL Improved module for php5
root@server:/home/andrei# dpkg -l | grep my
ii  libapache2-mod-auth-mysql    4.3.9-2ubuntu3            Apache 2 module for MySQL authentication
ii  libdbd-mysql-perl            3.0002-2build1            A Perl5 database interface to the MySQL data
ii  libmysqlclient15off          5.0.22-0ubuntu6.06.3      mysql database client library
ii  mysql-client-5.0             5.0.22-0ubuntu6.06.3      mysql database client binaries
ii  mysql-common                 5.0.22-0ubuntu6.06.3      mysql database common files (e.g. /etc/mysql
ii  mysql-server                 5.0.22-0ubuntu6.06.3      mysql database server (current version)
ii  mysql-server-5.0             5.0.22-0ubuntu6.06.3      mysql database server binaries
ii  netcat                       1.10-29                   TCP/IP swiss army knife
ii  php5-mysql                   5.1.2-1ubuntu3.8          MySQL module for php5
ii  php5-mysqli                  5.1.2-1ubuntu3.8          MySQL Improved module for php5
root@server:/home/andrenicolai# dpkg -l | grep apa
ii  apache2                      2.0.55-4ubuntu2.1         next generation, scalable, extendable web se
ii  apache2-common               2.0.55-4ubuntu2.1         next generation, scalable, extendable web se
ii  apache2-mpm-prefork          2.0.55-4ubuntu2.1         traditional model for Apache2
ii  apache2-utils                2.0.55-4ubuntu2.1         utility programs for webservers
ii  libapache2-mod-auth-mysql    4.3.9-2ubuntu3            Apache 2 module for MySQL authentication
ii  libapache2-mod-php5          5.1.2-1ubuntu3.8          server-side, HTML-embedded scripting languag
ii  libcap1                      1.10-14                   support for getting/setting POSIX.1e capabil

---

### Post by FleetAdmiral74 on 2007-06-16
I get this same problem when I don't have the correct repositories enabled. Do a quick search on universe and multiverse repositories, there is a text file somewhere were you just delete the commen ## and it enables the line. 

gl.

---

### Post by energiya on 2007-06-16
If you want to install everything yourself and not use [XAMPP]("http://www.apachefriends.org/en/xampp-linux.html") you could also try to install phpmyadmin from [http://www.phpmyadmin.net/home_page/index.php](http://www.phpmyadmin.net/home_page/index.php) :)

---

### Post by andre_n_costa on 2007-06-16
> **FleetAdmiral74 said:**
> I get this same problem when I don't have the correct repositories enabled. Do a quick search on universe and multiverse repositories, there is a text file somewhere were you just delete the commen ## and it enables the line. 

gl.

True! the sources.list was messed! fixed it, and now its working great! ubuntu rocks! 

thanks for the quick reply guys!

---

