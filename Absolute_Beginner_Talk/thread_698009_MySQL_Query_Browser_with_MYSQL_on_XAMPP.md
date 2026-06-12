---
title: "MySQL Query Browser with MYSQL on XAMPP"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by riutaro on 2008-02-15
Hi forum,

I am setting up MySQL on XAMMP.  What files should I edit in order to make MySQL Query Browser connect to the database?

When trying to connect to the localserver database, Query Browser returns an error.
```
Could not connect to host 'localhost'.
MySQL Error Nr. 2002
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```

Assuming that phpAdmin (this can, of course, connect to the databases created upon installing XAMMP) uses a socket under /opt/lampp/var/mysql/, I edited the my.cnf file in  /etc/mysql accordingly.
```
[client]
socket		= /opt/lampp/var/mysql/mysql.sock
```
This has enabled MySQL Administrator to connect to XAMPP example databases in /opt/lampp/var/mysql but Query Browser still attempts to use  /var/run/mysqld/mysqld.sock.

Aren't definitions in /etc/mysql/my.cnf global and every application should look at them?
:(

---

### Post by dustman on 2008-02-16
hello!

i think that the error is because your mysql server is not running. Try first to get it going, and only then connect to the server with the query browser ;)

Cheers!

Radu

---

### Post by riutaro on 2008-02-16
> **dustman said:**
> i think that the error is because your mysql server is not running. 
But I *think* my MySQL server is running.  I can use phpAdmin to operate on database tables.  I can connect to DBs with MySQL Administrator.

---

### Post by sunzaru on 2008-06-13
i'm getting the same thing.  i can connect via /opt/lampp/bin/mysql but not just mysql.  so there's something extra/hidden that i'm just not seeing.  i guess for now i'll just use phpMyAdmin

---

### Post by hezuo on 2008-07-20
You should try this:

$ sudo mkdir /var/run/mysqld
$ cd /var/run/mysqld
$ sudo ln -s /opt/lampp/var/mysql/mysql.sock mysqld.sock

It worked for me.

---

### Post by RicardoSchiller on 2008-07-21
Thanks hezuo!


Got mysql-admin and browser up and working!

---

### Post by hezuo on 2008-07-22
you're welcome :)

---

