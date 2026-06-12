---
title: "Can't connect with mysql"
date: 2005-10-05
forum: Absolute Beginner Talk
---

### Post by ErikaCruz on 2005-10-05
I have installed MySQL with XAMPP that installs all in one (Apache, MySQL and PHP).
Now I need to create the schema of a database with an script named database.sql.  My problem is that when I write in the Root Terminal 

root@ERIKA:~ # mysql -p database.sql

It shows the next message:

bash: mysql: command not found

MySQL is running since I started the whole XAMPP.  I am not sure wheter I need to configure something in MySQL or do I need to create a user or password?  What does it not recongnize the command mysql

---

### Post by fabiand on 2005-10-06
hey,

you need to install the mysql-client package.

- fabiand

---

### Post by matthewv on 2005-10-06
I think (and this is just pure conjecture) you might need to navigate to the mysql bin directory under your xampp install directory and run mysql from there, as, not having been installed, there will be nothing in /usr/bin or /bin or..

---

### Post by UbuWu on 2005-10-06
Type: 'locate mysql' to find out where it has been installed. Normally it should be in your path so you can just type 'mysql' to start it though.

---

### Post by matthewv on 2005-10-06
[QUOTE=UbuWu]Type: 'locate mysql' to find out where it has been installed. Normally it should be in your path so you can just type 'mysql' to start it though.[/QUOTE]

It normally would be in your path, but xampp comes as a tarball that can be extracted anywhere and then run from there... it is never "installed" i.e. deleting the xampp directory removes any trace of it ever having existed

---

