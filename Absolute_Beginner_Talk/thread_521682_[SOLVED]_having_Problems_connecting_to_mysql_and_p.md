---
title: "[SOLVED] having Problems connecting to mysql and phpmyadmin"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by uniquesolutions01 on 2007-08-09
I am having problems connecting to mysql database as a reqular user. the error i get is 

ERROR 1045 (28000): Access denied for user 'richboy01'@'localhost' (using password: Yes)

I am getting similar problem with phpmyadmin. Can anyone help. Thanks in advance.


Phillip

---

### Post by annda on 2007-08-09
have you set up mysql for the regular user (i.e. richboy01)? can you log in with

```
mysql -u root
```

---

### Post by uniquesolutions01 on 2007-08-09
I can log in with 
        **sudo mysql -u root -p**

but when i try sudo mysql **-u richboy01 -p **
 Thats when i get the error's.

I set up the new user in mysql with this query
           **INSERT INTO user (host, user, password, select_priv, insert_priv, update_priv) VALUES ('localhost', 'richboy01', PASSWORD('mypassword'), 'Y', 'Y', 'Y');**

then 
         **FLUSH PRIVILEGES;**

Phillip

---

### Post by annda on 2007-08-09
have you tried the standard grant_privileges command?

GRANT ALL PRIVILEGES ON *.* TO 'richboy01'@'localhost' IDENTIFIED BY 'mypassword' WITH GRANT OPTION;

this should work according to [documentation]("http://dev.mysql.com/doc/refman/5.1/en/adding-users.html") and my quick test.

---

### Post by uniquesolutions01 on 2007-08-09
WoW!!! You guys are the best. It worked. i can log into mysql and phpmyadmin Thank you very much. 



Phillip

---

