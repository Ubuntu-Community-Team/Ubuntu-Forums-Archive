---
title: "MySQL Question"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by rrkano on 2007-05-03
I've just installed Ubuntu 6.06 Server with mySQL, PHP etc. I set the root password for MySQL, created a database etc. Is there any way for me to access MySQL through SQL Enterprise Manager on a Windows PC? Or do I only have access to it via command line entry on the Ubuntu Server itself? Are there GUI utilities I can install to mange MySQL? 

Thanks

---

### Post by Cypher on 2007-05-03
I don't know about SQL Enterprise Manager, I'm going to guess no..

However, there's an awesome MySQL GUI called [phpMyAdmin]("http://www.phpmyadmin.net/home_page/index.php") that you should check out.

---

### Post by louieb on 2007-05-03
Like Cypher says phpmyadmin.  For every thing else theres [Webmin]("http://www.webmin.com/")

---

### Post by ukripper on 2007-05-23
Try XAMPP which is easier for admin includes phpmyadmin within and really easy to install

---

### Post by steve.horsley on 2007-05-23
Ubuntu repos contain mysql-admin and mysql-query-browser packages which are GUI applications you can use.

---

### Post by az on 2007-05-23
> **rrkano said:**
> I've just installed Ubuntu 6.06 Server with mySQL, PHP etc. I set the root password for MySQL, created a database etc. Is there any way for me to access MySQL through SQL Enterprise Manager on a Windows PC? Or do I only have access to it via command line entry on the Ubuntu Server itself? Are there GUI utilities I can install to mange MySQL? 

Thanks

Yes, you can access your mysql database remotely.  You need to set the bind address.  Whether the software you mention is compatible with mysq,. I dunno, never used it.

See here:


[https://help.ubuntu.com/community/ApacheMySQLPHP#head-2b91cc1ce37842102d20e88e029477b035bee150](https://help.ubuntu.com/community/ApacheMySQLPHP#head-2b91cc1ce37842102d20e88e029477b035bee150)



Also, stay away from xampp.

---

### Post by LaRoza on 2007-05-23
Why stay away from XAMPP? Sorry for butting in, but I would like to know.

---

### Post by tocleora on 2007-05-23
they have something called myodbc.  I'm not exactly sure if it works with Enterprise or not, but one of my coworkers uses it to connect to my mysql database through Access so there's a good chance it's possible.  I've also used it to develop visual basic apps so I know with it to some degree you *can* use microsoft products and mysql together.  

I think this is it:
[http://www.mysql.org/downloads/connector/odbc/3.51.html](http://www.mysql.org/downloads/connector/odbc/3.51.html)

---

### Post by az on 2007-05-23
> **LaRoza said:**
> Why stay away from XAMPP? Sorry for butting in, but I would like to know.

It's a toy.  It's not to be used in a production environment.  Especially with how trivially easy it is to install and run a LAMP stack on Ubuntu.  Using the packages from Ubuntu, you get proper support with security vulnerability and bug fixes.

---

### Post by tocleora on 2007-05-24
> **az said:**
> It's a toy.  It's not to be used in a production environment.  Especially with how trivially easy it is to install and run a LAMP stack on Ubuntu.  Using the packages from Ubuntu, you get proper support with security vulnerability and bug fixes.

I have to agree, I've tried to use it on multiple occasions and although it's easy to install it's not as easy to upgrade or do customization with (especially if you're relying on documentation from other sources) depending on what distro/os you're using.  It's too easy to install LAMP to not use it.

---

### Post by hyper_ch on 2007-05-24
I think by default mysql access is localhost only... you will need to change that to connect to mysql from a remove connection...

---

### Post by LaRoza on 2007-05-24
I use XAMPP, for Windows, on my flash drive because it is portable and I can do Web developement where ever I am, school, home, other peoples computers, my other computer. I never thought it would be used on a computer instead of a flash drive.

---

