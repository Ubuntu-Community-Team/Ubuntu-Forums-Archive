---
title: "mysql - nothing fancy."
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by richieboy on 2007-06-21
i bought an o'reilly book called "baseball hacks".  it gives instruction for setting up a database of baseball stats but not for setting up mysql.  the idea is to have client and server on the same machine and manipulate the databases that way.  i downloaded mysql from synaptic.  NOW WHAT?  how do i set up a root password? a user account?  how do i do anything?  i can't make his examples work.

please help.

rich

---

### Post by silverglade00 on 2007-06-21
You probably also want to install phpMyAdmin and apache. This will give you a web browser based interface to mysql. If the book gives you command line commands, then the way to start the mysql prompt can be reached by opening the terminal end typing mysqladmin

Good luck!

---

### Post by Bachstelze on 2007-06-21
To install the MySQL server :

```
sudo apt-get install mysql-server-5.0
```

(you can also install *mysql-server-4.1* if you wish)

To initialize the server (i.e. create a root password and the like) :

```
sudo /usr/bin/mytsql_secure_installation
```

For a nice tutorial to get you started :

[http://dev.mysql.com/doc/refman/5.0/en/tutorial.html](http://dev.mysql.com/doc/refman/5.0/en/tutorial.html)

---

