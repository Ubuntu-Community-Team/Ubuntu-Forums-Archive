---
title: "mysql s.o.s"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by regiszt on 2007-03-08
I was a little bit stupid and I did this procedure on a fresh mysql:

# mysql -u root mysql

Afterthat I changed the root password which was successfull, and here comes the funny thing:

#drop database mysql;

and exit

now, after reboot the mysql service starting is fail and I can't do anything in connection with mysql

Could you tell me what to do?

---

### Post by ziggykg on 2007-03-08
Guess what?  You're missing the 'mysql' database which you apparently dropped.  It's a vital part of MySql as it contains, among other things, the root user's details, table/database privilege info.

I suggest you reinstall MySQL.  You can do this using Synaptic

---

### Post by regiszt on 2007-03-08
Great idea but I just have used this : mysql_install_db 
It created a new database !!!

---

### Post by ahsile on 2007-03-08
In the future, don't touch the mysql database :) This is one of the many reasons NOT to run as root. Set a password on the root account, and then make sure to set up a personal user account ASAP and don't give yourself access to muck with the mysql db.

---

