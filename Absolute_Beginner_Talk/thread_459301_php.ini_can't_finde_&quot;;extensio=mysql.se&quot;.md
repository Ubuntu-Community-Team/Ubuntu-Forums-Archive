---
title: "php.ini can't finde &quot;;extensio=mysql.se&quot;"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by durus on 2007-05-30
Hi 
I'm following the tutorial on [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Apache_HTTP_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Apache_HTTP_Server) for installing apache2 web server with php5 and mysql. I have done all steps but i can't find ;extension=mysql.so in php.ini file located at  /etc/php5/apache2/php.ini.
I have used php in windows and as i can remember, there should be a lot of extension that i should be able to uncomment, but i cant find any ";extension=*" in my php.ini file.
Do you see something strange in that tutorial.
I have used this commands:

```
sudo apt-get install apache2
sudo a2enmod userdir

sudo apt-get install php5
sudo apt-get install libapache2-mod-php5
sudo /etc/init.d/apache2 restart

sudo apt-get install php5-xsl php5-gd php-pear
sudo /etc/init.d/apache2 restart

sudo apt-get install libapache2-mod-auth-mysql
sudo apt-get install php5-mysql
sudo aptitude install phpmyadmin
gksudo gedit /etc/php5/apache2/php.ini
```

And I cant find any ;extensio=mysql.so in this file to uncomment

---

### Post by annda on 2007-05-30
so your php doesn't work with mysql?

you do have the line with the extension, but it doesn't need to be uncommented, php5-mysql should take care of that. have you tested your configuration first?

---

