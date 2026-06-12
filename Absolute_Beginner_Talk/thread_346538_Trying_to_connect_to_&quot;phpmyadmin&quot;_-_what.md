---
title: "Trying to connect to &quot;phpmyadmin&quot; - what is the default username &amp; password to use?"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2007-01-25
Hello!

I have managed to install "phpmyadmin".
When I launch a Web Browser window & type "http://localhost/phpmyadmin" I get on the log-in page.
The problem is that I don't know what the default username & password are... :(
Anybody know what the factory/default username & password for "phpmyadmin" is?

Thanks.

---

### Post by DSn0wMan on 2007-01-25
You should enter your MYSQL credentials.

---

### Post by mitchi on 2007-10-09
Even the defaults for mysql username and password is unknown. What are the default values? 

BTW, I'm using 7.04 Feisty Fawn when I installed MySQL.

---

### Post by hyper_ch on 2007-10-09
You first need to set a mysql root password:

```

sudo mysqladmin -u root password YOURMYSQLROOTPASSWORD

```
After that you can login as root / YOURMYSQLROOTPASSWORD into phpMyAdmin. Once done, you can add more users to it and link it to specific databases (if desired) or even specific tables within databases.

---

### Post by mitchi on 2007-10-09
it just replied:

> 
$ sudo mysqladmin -u root password YOURMYSQLROOTPASSWORD
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!



what to do now?

---

### Post by hyper_ch on 2007-10-09
do you have mysql server installed?

---

### Post by mitchi on 2007-10-09
i just installed it, sorry. it works now fine.

thank you very much.

---

### Post by mitchi on 2007-10-09
the password seems to be very long. How can change the password?

thanks..

---

