---
title: "install apache2, php and mysql on Ubuntu 5.10"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by herbert tamayo on 2006-11-21
Hi to all, i`m using ubuntu 5.10 in a 300 mhz with 128 RAM, ok, I have real troubles trying to install apache, php and mysql in ubuntu, the CD only comes with the common files of apache and mysql, nothing about php.

So, browsing the web, in packages.debian.org I´m trying to download the packages and their dependences but my problem is that there`s to many dependences to download at once.

I can´t upgrade to ubuntu 6.10 because my cpu only has 128 RAM and I can´t find DIMM RAM in the market, besides, it´s the computer of my office.

And my last problem it´s that in that machine doesn´t have an internet connection, so I have to download the package

So, I need that LAMP works in 5.10, can you help me giving me some advice? I really need to work those packages.

Thanks

---

### Post by adamkane on 2006-11-21
This will get you started.

Install LAMP (Linux + Apache2 + MySQL + PHP), then acess MySQL database from phpmyadmin webpage.

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```Reboot (or start mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]
----------------------------------
You can also install xampp, if you want the latest LAMP available.

---

