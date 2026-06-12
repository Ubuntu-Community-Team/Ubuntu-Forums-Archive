---
title: "[SOLVED] Joomla"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-04-18
I'm trying to install it
but i don't know what to put into the spaces... screenshot below

---

### Post by Frequent Modulation on 2008-04-18
This may help you.

[http://help.joomla.org/ghop/feb2008/task048/joomla_15_quickstart.pdf](http://help.joomla.org/ghop/feb2008/task048/joomla_15_quickstart.pdf)

page 8

---

### Post by Confuzius on 2008-04-18
Make sure you have mysql installed on your server.

I find it easiest to install "phpmyadmin" to mange mysql databases, basically you need a new mysql database for joomla and a mysql user that has the rights to edit the database.

More info here:
[http://www.phpmyadmin.net/home_page/index.php](http://www.phpmyadmin.net/home_page/index.php)

Then you put that info into the joomla setup.

---

### Post by msayed2004 on 2008-04-18
I guess the MySQL User name & Password will be equal to your log-in name & password, If you get an error then use the following command to reset the password:
```
sudo dpkg-reconfigure mysql-server-5.0
```For the database name you need to create a MySQL database first.

Can you install [webmin]("http://www.webmin.com/") to handle everything via GUI ? This will make stuff easier :D

---

### Post by RadiationHazard on 2008-04-18
are the mysl username and the mysl database name the same?

---

### Post by RadiationHazard on 2008-04-18
i got it thanks :)


[SIZE="5"]**[COLOR="Red"]****NeverMind!!****[/COLOR]**[/SIZE]

---

### Post by RadiationHazard on 2008-04-18
moved to new thread

---

