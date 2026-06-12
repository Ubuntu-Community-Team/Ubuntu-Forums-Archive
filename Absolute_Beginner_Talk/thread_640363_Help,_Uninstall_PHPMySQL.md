---
title: "Help, Uninstall PHP/MySQL"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by teuma on 2007-12-14
I run the following to install LAMP settings

sudo apt-get install apache3
sudo apt-get install php5
sudo apt-get install php5-mysql
sudo apt-get install php5-curl

Then I went to the Application Manager to try and find a GUI for MySQL (Instead of PHPMyAdmin)

Now, I can not connect to mysql

I am trying to remove the above

I run the following

sudo apt-get remove php5-curl
sudo apt-get remove php5-mysql
sudo apt-get remove php5
sudo apt-get autoremove php5 

PHP STILLL works on my laptop

I have done a reboot

Any suggestions on how to remove all completly so i can add a clean install

---

### Post by jken146 on 2007-12-14
```
sudo apt-get remove --purge <package>
``` OR ```
sudo aptitude remove <package>
```

---

### Post by hyper_ch on 2007-12-14
and also restart apache

---

