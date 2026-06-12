---
title: "Amarok setup with mysql"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by walt+walt on 2007-07-06
I have tried the how-to's (the ones I have found in various topics here)  with their different ways to configure mysql for amarok.

I think I got pretty far, but keep stopping at the password-entry. A selection of resulting system-messages are shown here:
----------------------------------------------------------------------------------------
root@ubuntu:~# mysqladmin -u root -p create amarok
Enter password:
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: YES)'
root@ubuntu:~# mysqladmin -u root -p create amarok
Enter password:
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
root@ubuntu:~# mysql -u root -p
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
root@ubuntu:~# mysql -u root -p
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
------------------------------------------------------------------------------------------------

I do run feisty on desktop. I also reinstalled MySql a couple of times - cause I thought the prob is better solved with a blank version: As Password I always used my root-password (single-machine - songle user).

Really, I have tried many forums but never found the clue.

Well, I finally run out of ideas and think, I will just need the following infos and steps (===> for an amateur):

-> system is feisty
-> kubuntu
-> amarok 1.4.6

-> I am the single user on this machine (for the moment)  have rootpsw (obviuosly)
-> user-name would be walt with same psw as root-psw

-> I can setup sql-server
-> but I cant enter sql-admin

-> please, all I do need is a simple tutorial to setup mysql for amarok.

Hope anybody can help me. Many many thanks in advance, walt in trouble

---

### Post by DSn0wMan on 2007-07-06
Your mysql root password is set when you install mysql. If you can not remember it you will need to reset it. I have used these instructions in the past to sucessfully reset the mysql root password.

[http://ubuntu.flowconsult.at/en/mysql-set-change-reset-root-password/](http://ubuntu.flowconsult.at/en/mysql-set-change-reset-root-password/)

---

### Post by testube_babies on 2007-07-06
I set it up with mysql using this tutorial...works every time:
[http://amarok.kde.org/wiki/MySQL_HowTo](http://amarok.kde.org/wiki/MySQL_HowTo)

---

