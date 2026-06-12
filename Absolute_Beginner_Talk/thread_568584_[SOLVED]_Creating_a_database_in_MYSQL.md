---
title: "[SOLVED] Creating a database in MYSQL"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by High Camp on 2007-10-06
Hi All

I'm trying to set up Egroupware. I've done everything but create the MYSQL database. When I went to do it I got the following error:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

I've looked at:
[http://www.debuntu.org/how-to-create-a-mysql-database-and-set-privileges-to-a-user](http://www.debuntu.org/how-to-create-a-mysql-database-and-set-privileges-to-a-user)
[http://forums.mysql.com/read.php?11,9689,16123#msg-16123](http://forums.mysql.com/read.php?11,9689,16123#msg-16123)
[http://ubuntuforums.org/showthread.php?t=252401](http://ubuntuforums.org/showthread.php?t=252401)
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

All of those are great resources but they don't have any trouble shooting ideas. From what I know so far (I'm a Linux and SQL newb) there is no socket to connect to. I went a looked and the folder msqld and it doesn't exist so I suspect that the prob. I assume I need to move all of the SQL stuff to that folder or create a link to the location.

Any thoughts on what I need to do?

P.S. if it helps, I'm running Xubuntu.

Thanks much,

P.P.S. I noticed OO can deal with SQL databases. Can I use that to mess around with the database?

---

### Post by Hugolp on 2007-10-06
Hi

I had the same problem and I ended up creating the database myself. I just created it empty and the egroupware installation filled it.

If you are new to mysql I recomend you use phpmyadmin. Its the easiest way to edit your mysql.

Hugo

---

### Post by High Camp on 2007-10-06
Hey Hugo

Thanks for the reply. I'll have to wait until I'm at home to try it on the server.

I do have some questions about Egroupware if you can take a few seconds to answer them. My biggest question is if you have set up sync with palm devices. That is the main reason to have a groupware solution. If you have set it up how hard was it and do you have any resources you can share?

Thanks again for the reply.

---

### Post by High Camp on 2007-10-08
Ok, I'm the first to admit, I'm a dumbass. It turns out MYSQL wasn't even installed. I made the dumb assumption that if I installed the tools Synaptic would be install it.

Sorry to waste everyone's time.

---

