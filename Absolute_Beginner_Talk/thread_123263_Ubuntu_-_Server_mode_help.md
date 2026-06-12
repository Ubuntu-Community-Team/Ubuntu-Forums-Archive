---
title: "Ubuntu - Server mode help"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by v8cortina on 2006-01-29
Hi,
Totally new to Linux so apologies for any stupid questions.  My aim is to configure a Web Server using Ubuntu Version 5.10 with Apache, PHP and MySQL. This will only be used at home and not open to the www.
I have installed Ubuntu and chose Server at the boot prompt. Everything installed OK first time.  Here are my two questions -
1. Is there a graphical desktop I can use in Server mode, if there is how do I start it up?
2. Where or how can I find what is installed during the Server setup? e.g. maybe Apache was installed as default, how do I check.

Hope someone can assist.  

Regards
Thierry

---

### Post by hen3rz on 2006-01-29
> 1. Is there a graphical desktop I can use in Server mode, if there is how do I start it up?

Server mode is pure text based with no gui.

> 2. Where or how can I find what is installed during the Server setup? e.g. maybe Apache was installed as default, how do I check.

I can tell you now that apache does not install default and unfortunateley I do not know of a way to check what has been. To install apache php mysql you can run the following commands.

```
sudo apt-get install mysql-server
sudo apt-get install apache2
sudo apt-get install php5
sudo apt-get install php5-mysql
sudo apt-get install phpmyadmin
```

---

### Post by v8cortina on 2006-01-29
Many thanks for your help.  This will have saved me hours of searching and pulling my hair out.  I will try this out tomorrow.

First Class.

---

### Post by tim15856 on 2006-01-29
No GUI is installed with the server install. If you need a GUI, use the command "sudo apt-get install ubuntu-desktop" or sub Kubuntu if you want KDE instead of Gnome.

---

### Post by nerosero on 2006-01-30
Hi,
im new to Linux so i apologies for any stupid questions.

I manige to do install 


mysql-server
apache2
php5
php5-mysql

But i cant install phpMyAmdin 

i get this ERROR msg 

root@XPC:/home/MYname# sudo apt-get install phpmyadmin
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package phpmyadmin
root@XPC:/home/MYname# sudo apt-get install phpmyadmin
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package phpmyadmin
root@XPC:/home/MYname# sudo apt-get install phpmyadmin
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package phpmyadmin

how can I install phpMyAdmin??? 

PLS Help me

Regards
nerosero ( Iceland ):D

---

### Post by kaamos on 2006-01-30
You might want to read this: [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)
Make sure you also follow the AddingRepositoriesHowto-link.

---

### Post by nerosero on 2006-01-30
Danke :)

---

