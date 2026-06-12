---
title: "Apache - I can't find www folder in /var"
date: 2005-10-03
forum: Absolute Beginner Talk
---

### Post by ErikaCruz on 2005-10-03
I installed XAMPP from [www.apachefriends.org](www.apachefriends.org).  It installs Apache 2.0.54 , MySql 4.1.13 and PHP 5.0.4.  Does the www folder is created when apache is installed or it has to be created for me manually into /var/ ? I need to install Aria, a web SW and it asks me to setup DocumentRoot "/var/www/aria" but I went to the /var directory and I don't see a www folder.  Thanks for your help.

---

### Post by matthewv on 2005-10-03
If you followed the instructions on the XAMPP site XAMPP will be installed in /opt/lampp. Go to a terminal and type "sudo gedit /opt/lampp/etc/httpd.conf" to edit your apache config file. Change the variable DocumentRoot to /var/www/aria and save. If the folder does not exist create it.

---

### Post by ErikaCruz on 2005-10-03
Thanks Matthew.  One more question. Aria is also asking me to make sure that the index.php exists but the only index that I found was index.html.  Then they give an example

DirectoryIndex index.php index.html index.html.var

Is DirectoryIndex a command or does this create the index.php?

Thanks for your help

---

### Post by matthewv on 2005-10-03
Does it ask you to make sure it exists before or after the installation??

---

### Post by matthewv on 2005-10-03
Think I've got it now:

DirectoryIndex is an Apache option that determines what page the webserver will open when you navigate to a folder. This variable is also inside the /opt/lampp/etc/httpd.conf file. Make sure that index.php is listed or the program's 'home page' will not be found.

---

