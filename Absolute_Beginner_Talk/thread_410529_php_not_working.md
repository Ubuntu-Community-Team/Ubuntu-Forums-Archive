---
title: "php not working"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by ProjectWhat on 2007-04-15
Ok apache2 works fine but when i click on a php file it doesnt work. I wants me to save it to my computer. i did a "sudo /etc/init.d/apache2 restart" but that didnt help.

---

### Post by motin on 2007-04-15
> **ProjectWhat said:**
> Ok apache2 works fine but when i click on a php file it doesnt work. I wants me to save it to my computer. i did a "sudo /etc/init.d/apache2 restart" but that didnt help.

You have to install php as well. php5, apache2-mod-php5 similarly named packages are the key. 

Then you'll have to access the php files through a browser - not double-clicking in Gnome etc - but I guess you knew that.

---

### Post by ProjectWhat on 2007-04-15
> **motin said:**
> You have to install php as well. php5, apache2-mod-php5 similarly named packages are the key. 

Then you'll have to access the php files through a browser - not double-clicking in Gnome etc - but I guess you knew that.

i have already done apache2-mod-php5, but sudo apt-get install php does not install anyhting

---

### Post by bobplano on 2007-04-15
the package for php is php5 because there are different versions

---

### Post by ProjectWhat on 2007-04-15
ok well i have done all that and still it doesnt work.

---

### Post by speeves on 2007-04-15
The correct package is:

sudo apt-get install libapache2-mod-php5 

And, don't forget to:

sudo a2enmod php5

Then restart apache2:

sudo /etc/init.d/apache2 restart

---

### Post by ProjectWhat on 2007-04-15
Yes i understand that and have already done that. 
```
ben@Ben-Ubuntu:~$ sudo apt-get install libapache2-mod-php5 
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libapache2-mod-php5 is already the newest version.
The following packages were automatically installed and are no longer required:
  libopenexr2c2a libarts1c2a libartsc0 kdelibs-data liblualib50 libavahi-qt3-1
  libqt3-mt liblua50
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ben@Ben-Ubuntu:~$ sudo a2enmod php5
This module is already enabled!
ben@Ben-Ubuntu:~$ sudo /etc/init.d/apache2 restart
ben@Ben-Ubuntu:~$ 

```
And it still dosnt work
Is there some kind of conf file that has to be edited?

---

