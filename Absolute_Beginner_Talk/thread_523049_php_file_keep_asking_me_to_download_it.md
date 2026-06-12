---
title: "php file keep asking me to download it"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by tungv0 on 2007-08-11
I have tried to install LAMP as the instruction here: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
However, when I open the php file, instead of displaying the browser keep asking me to download the file. I have thought that the installation of libapache2-mod-php5 is corrupted so I have remove and re-install it again but the problem still remain. Can someone please suggest me how to solve this?

Many Thanks

---

### Post by geek_Man on 2007-08-11
Add the following into your /etc/apache2/apache2.conf file: ```
DirectoryIndex index.php index.html

AddType text/html       php
```

That'll help it to recognize PHP files. HTH

---

### Post by tungv0 on 2007-08-13
sorry for the late reply. Where should I add those 2 line in the configuration file of apache2? Do I need to add those 2 line in a specific place or anywhere is fine?

---

### Post by tungv0 on 2007-08-13
I have added those 2 lines at the end of /etc/apache2/apache2.conf, and restart the apache2. However when I open the *.php file, it still asking me to download it. Dose anyone know how to solve this?

---

### Post by geek_Man on 2007-08-13
I have it right under where it says ServerRoot. 

Sorry, this is a stupid question, but are you sure that you have php5 installed?

---

### Post by geek_Man on 2007-08-13
Oh, I forgot! You have to restart Apache. Type "apache2 --restart", that should do it.

---

### Post by tungv0 on 2007-08-14
well, I did install php5 as well as libapache2-mod-php5, I also restart apache2. Basically I have followed the instruction here: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP), step by step (I did not use tasksel to install LAMP as somehow it does not work). By the way my ubuntu is 7.04. Can you help me to figure out what's wrong with it?

---

### Post by az on 2007-08-14
Exactly what apache, php and mysql packages do you currently have installed?  List them all.

---

### Post by tungv0 on 2007-08-14
I have installed apache2, php5, mysql-server and some extra packages as libapache2-mod-php5, libapache2-mod-auth-mysql, php5-mysql

---

### Post by az on 2007-08-14
> **tungv0 said:**
> I have installed apache2, php5, mysql-server and some extra packages as libapache2-mod-php5, libapache2-mod-auth-mysql, php5-mysql

What is the output of

dpkg -l|grep apache


I'm wondering if you inadvertently installed both apache and apache2.

---

### Post by dashnak on 2007-08-14
I had the same problem once, took about a week to fix. Try this:
```
sudo a2enmod php5
```And then restart apache, let us know if it works.

---

### Post by tungv0 on 2007-08-15
here is the result of: dpkg -l|grep apache

ii  apache2                                    2.2.3-3.2build1                        Next generation, scalable, extendable web se
ii  apache2-mpm-prefork                        2.2.3-3.2build1                        Traditional model for Apache HTTPD 2.1
ii  apache2-utils                              2.2.3-3.2build1                        utility programs for webservers
ii  apache2.2-common                           2.2.3-3.2build1                        Next generation, scalable, extendable web se
ii  libapache2-mod-auth-mysql                  4.3.9-2.1ubuntu2                       Apache 2 module for MySQL authentication
ii  libapache2-mod-php5                        5.2.1-0ubuntu1.4                       server-side, HTML-embedded scripting languag

---

### Post by tungv0 on 2007-08-15
to Dasknak: I have also tried that but it does not work. When I run sudo en2mod php5, it says this module is already enable, and after restarting apache2, php file still asking me to download it

---

### Post by dashnak on 2007-08-16
Mhhhh, that's weird...

---

### Post by tungv0 on 2007-08-16
hic I also have no idea about this. I have installed LAMP before with my laptop, but this time it's really strange with my desktop

---

