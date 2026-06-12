---
title: "MySQL not starting?"
date: 2005-10-03
forum: Absolute Beginner Talk
---

### Post by morficus on 2005-10-03
I've been following [this website]("http://www.devside.net/web/server/linux/mysql") to install MySQL.

Everythig was going fine until the last part "Runing MySQL"
this is the error I get..
> root@morf-serv:/usr/local/mysql/bin# ./mysql -umysql -p
Enter password:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)


I don't really know what pswd to use... ''cause up to now I haven't set any password for MySQL.

any clue what I'm doing wrong?
or maybe have another tutorial as of how to install MySQL??

thanx (3rd post for the day - man am I anoying :p )

-morficus

---

### Post by Wide on 2005-10-03
You can use the Synaptic Package manager in Ubuntu to install it without a hitch


System>Administration>Synaptic Package Manager

If your want a full LAMP (Linux Apache, Mysql, PHP) setup there are a ton of examples here in the forums


:D

---

### Post by morficus on 2005-10-03
but the stuff I get from Synaptic Package Manager is just client-side, is it not?

---

### Post by Buffalo Soldier on 2005-10-04
Just installed MySQL using Ubuntu repositories: **mysql-server** and **mysql-client**. At the end of the installation it will run a basic setup script.

---

