---
title: "LAMP issues"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2008-03-03
I am running ubuntu 7.10 and having installed apache/mysql/php as followed:

sudo apt-get install apache2
sudo apt-get install php5
/etc/init.d/apache2 restart (successful)
sudo apt-get install mysql-server
sudo apt-get install php5-mysql
/etc/init.d/apache2 restart (successful)

I then try to load a php file from my localhost and i get a download prompt.  is there anything i missing in installing this?

---

### Post by Roanoke on 2008-03-04
From which browser are you loading the file? Try firefox, if anything else.

---

### Post by Oldsoldier2003 on 2008-03-04
> **RyanZec said:**
> I am running ubuntu 7.10 and having installed apache/mysql/php as followed:

sudo apt-get install apache2
sudo apt-get install php5
/etc/init.d/apache2 restart (successful)
sudo apt-get install mysql-server
sudo apt-get install php5-mysql
/etc/init.d/apache2 restart (successful)

I then try to load a php file from my localhost and i get a download prompt.  is there anything i missing in installing this?
you need to read the docs and configure Apache to parse php files.

try a2enmod php5
then look at your php config and your sites enabled.

---

### Post by RyanZec on 2008-03-04
it tells me that the php5 module does not exist even tho I have the libapache2-mod-php5 installed.

---

