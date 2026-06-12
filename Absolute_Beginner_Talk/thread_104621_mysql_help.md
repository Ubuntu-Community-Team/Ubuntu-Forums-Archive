---
title: "mysql help"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by grim918 on 2005-12-16
i just installed apache php and mysql. im having a problem with the mysql database. when i try to create a new database it tells me that i need a password. i installed mysql with:
sudo apt-get install mysql-server

i dont remember ever entering a password. does anyone know if theres a default password or where i can change the password. or maybe i just did the whole installation wrong. either way i could really use some help.

---

### Post by kalin on 2005-12-16
Look here:
[http://www.linuxhelp.net/guides/mysql/](http://www.linuxhelp.net/guides/mysql/)

Basically, you want to set the password first, using this command:

```

mysqladmin -u root password 'passwordyouwant'

```

---

### Post by grim918 on 2005-12-19
i have been trying to set my password for MySQL database but i keep on getting errors.
this is the error that i get when i try to change my password

:~$ mysqladmin -u root password 'password'
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: NO)'

i also tried using sudo to see if that would work but i still get the same errors. can someone please help me out.

---

### Post by ertai on 2005-12-19
what do you get when you type

'mysql -u root'

when you can't login the password is probably set. Then you should try to login with

'mysql -u root -p'

and then use as password the first password you tried to set

---

### Post by grim918 on 2005-12-20
thank you i got it working.

---

