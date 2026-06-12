---
title: "MySQL Server Installation Issue"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by chrisf79 on 2007-07-25
Greetings,

I just installed mysql-server using apt-get but I'm having some issues.  I went in with mysql -u root and that started it up fine.

I then typed:  SET PASSWORD FOR 'root'@'localhost' = PASSWORD('yourpassword');

Of course, I replaced yourpassword with my password.

Anyway, I get:  Query OK, 0 rows affected (0.00 sec)

It isn't working evidently!  Now my problem is that I accidentally closed that terminal window and I can't even try again!  When I run mysql -u root now, I get ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

So that leaves me with a few questions.  How can I get back in to my MySQL and once I'm in, what am I doing wrong to set my root password?  Any help would be greatly appreciated!

---

### Post by annda on 2007-07-25
have you tried
```

mysql -u root -p
```

this should give you a prompt for the password. but then again, this "0 rows affected" message is a bad sign...

---

### Post by chrisf79 on 2007-07-25
I really have no idea how to set the root password.  Can you see anythign wrong in what I tried the first time?

---

### Post by az on 2007-07-25
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

mysql password reset:
[https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)

---

### Post by chrisf79 on 2007-07-25
> **az said:**
> 
mysql password reset:
[https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)
Thanks SO much!  That password reset worked like a charm!

---

