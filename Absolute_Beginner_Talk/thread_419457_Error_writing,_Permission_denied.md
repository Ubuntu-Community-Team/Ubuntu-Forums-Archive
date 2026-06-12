---
title: "Error writing, Permission denied"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by karla on 2007-04-23
Hi,
I am just finished installing LAMP according to instructions ([http://ubuntuforums.org/newthread.php?do=newthread&f=73)](http://ubuntuforums.org/newthread.php?do=newthread&f=73)).
When I try to edit a conf file with (nano /etc/mysql/my.cnf -command) to change the bind-address           = my machine IP, I don't seem to have the permission to edit and save this file.
Any suggestion - what to do?

/Karl

---

### Post by simonn on 2007-04-23
```

$ sudo nano /etc/mysql/my.cnf

```

---

### Post by kvonb on 2007-04-23
You have to temporarily get super user privileges, like so:

Either in a terminal, type this:

```
sudo nano /etc/mysql/my.cnf
```or another method from the desktop is to press <ALT><F2>, and in the pop-up box type:

> gksu nano /etc/mysql/my.cnfYou will need to do this for just about ANY file that is outside your ~/ (home) folder, and especially if it is a system config file, ie anything in the /etc folder.

This is one of the reasons that viruses (should that be virii?) have a hard time under Linux, you can't just modify/delete anything without suitable privileges :).

---

