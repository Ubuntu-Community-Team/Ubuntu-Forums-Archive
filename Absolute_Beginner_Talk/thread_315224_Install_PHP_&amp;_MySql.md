---
title: "Install PHP &amp; MySql"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by Captain Kirk76 on 2006-12-08
I develop a few sites, and as such i need PHP & MySql installing, where can i get these from? On Windows i use [Xammp](http://www.apachefriends.org/en/xampp.html) an all in one package with Apache PHP & Mysql, is there a similar thing for Ubuntu, or if not, how else can i get them. (PHP Especially, the other don't overly matter)

---

### Post by Paul41 on 2006-12-08
I am not sure about an all in one, but these are all available in the repository.

For php:
```
sudo aptitude install php5
```

For MySql:
```
sudo aptitude install mysql-server
```

for Apache:
```
sudo aptitude install apache2
```

---

### Post by az on 2006-12-08
> **Captain Kirk76 said:**
> I develop a few sites, and as such i need PHP & MySql installing, where can i get these from? On Windows i use [Xammp](http://www.apachefriends.org/en/xampp.html) an all in one package with Apache PHP & Mysql, is there a similar thing for Ubuntu, or if not, how else can i get them. (PHP Especially, the other don't overly matter)

To get the LAMP stack install
apache2 php5-mysql libapache2-mod-php5 mysql-server

See here:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Captain Kirk76 on 2006-12-09
i used sudo aptitude, where exactly does it put htdocs, the folder where i put my stuff to go online?

---

### Post by az on 2006-12-09
> **Captain Kirk76 said:**
> i used sudo aptitude, 

It doesn't matter what you use to install it - apt-get aptitude, whatever..

> **Captain Kirk76 said:**
> 
where exactly does it put htdocs, the folder where i put my stuff to go online?

/var/www/apache-default

set your sites in /etc/apache2/sites-available/
and enable them with
sudo a2ensite

---

