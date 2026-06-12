---
title: "mysql server help needed plz"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by pedrotuga on 2005-12-16
My mysql server is running fine.... phpmyadmin works perfectly through apache.

but when i tryed to use mysql administrator in other computer it doesnt work... why the heck cant i connect the database from the outside?

thx in advance

---

### Post by philwozza on 2005-12-20
Are you still having this problem?

What exactly is the error you are getting from the MySQL administrator?


It could be that MySQL by default will only listen for connections originating from the computer that the MySQL database is running on.  I think this is the case at least for MySQL 4.1 on Ubuntu.

You can make MySQL listen for connections on all addresses by editing a configuration file.

sudo nano sudo nano /etc/mysql/my.cnf

Look for the line 

# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address            = 127.0.0.1

and change it to

# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
# bind-address            = 127.0.0.1

Hold CTRL and press the X button to save. When asked where to save the file simply press return.

Now you will need to resart MySQL to activate the new configuration. Use the command.

sudo /etc/init.d/mysql restart


Let me know how you get one

---

### Post by pedrotuga on 2006-02-24
forgot to came here and thank.

I solve the problem by changing permitions on mysql users with grant statements.

For those with the same problem u can read the instructions on the mysql manual here:

[http://dev.mysql.com/doc/refman/5.0/en/adding-users.html](http://dev.mysql.com/doc/refman/5.0/en/adding-users.html)

Or in alternative log in with phpmyadmin, if you have it installed of course, as "debian-sys-main" the password is the same as the system root. Then change the permitions to the user u want to have access worldwide. the wildcard is '%'.

Thank you philwozza

---

