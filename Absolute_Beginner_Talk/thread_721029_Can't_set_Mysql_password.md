---
title: "Can't set Mysql password"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by jpates20 on 2008-03-10
can't seem to set the password in mysql its on my gnome besktop,im running 6.06 LTS , can some one help me? Im running on a dell power edge 2500 raid server...thanks

---

### Post by mmichalik on 2008-03-10
If you are trying to set your MySQL root password for the 1st time, it goes like this: (open a terminal and at the command line type the following)

cd /urs/bin

mysqladmin -u root password 'your_new_root_password'

change the your_new_root_password to what ever you want the password to be but, leave the surrounding tic marks ' as they need to be there.

press enter

and you should be set from there.

---

### Post by jpates20 on 2008-03-11
I tryed that, but all i get is this!!



mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
root@spyman-desktop:/home/spyman#

---

### Post by haryoh on 2008-03-11
if you are a root

first, mysql as a table in it after installation, it's called mysql (TABLE).
type: show databases;
then type: describe (mysql-table after you found it)

type: mysql -u root -p 'PASSWORD' (from the terminal without locating a path)

then type the following to change your password for root:

mysql> update mysql.user set password = PASSWORD('whateverpassword') where user = 'root';

then type:
mysql> flush privileges;

the same way can be done to change users passwords or usernames.

Hope this is helpful.

---

### Post by ung/xunil on 2008-03-11
Debian has its tricks for this things. Since you are using Ubuntu 6.06 LTS (dapper) you should try:
```
sudo /etc/init.d/mysql reset-password
```
That should work until Ubuntu 7.04 Feisty (dapper-edgy-feisty).

Starting with Ubuntu 7.10 Gutsy, resetting the mysql password can/should be done via dpkg (it was included there so the root mysql password is set on install and to never be left unset):
```
sudo dpkg-reconfigure mysql-server-5.0
```

---

### Post by mmichalik on 2008-03-11
ung/xunil

Those are GREAT tips to know.

Thanks for posting them.

---

### Post by Dusal on 2008-05-10
Thank you very much :D

---

