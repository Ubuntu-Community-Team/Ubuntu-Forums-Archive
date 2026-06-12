---
title: "phpmyadmin"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Frequent Modulation on 2008-04-20
im attempting to login to phpmyadmin through localhost/phpmyadmin. I am getting prompted for user name and password. Which file has this information? I cant remember if i set this up or not but have tried every combination of user/password with no success. 
I have looked in the my.cnf file and the config.inc.php file. 

Your help will be appreciated

---

### Post by KingWilliam on 2008-04-21
Hi there, 

The login prompted by phpMyAdmin is the one for your mySQL database. So if you login with (root/password) in MySQL then (root/password) is what you should enter to log in with phpMyAdmin. But of course it is best to create an other user in mySQL so you don't need to use root. If you need any help with that don't hesitate to ask...

Grtz, 

KW

---

### Post by demzed on 2008-04-25
Hi, i have the same problem, i cant login. I tryed all kinds of users, then i tryed 'root' but i still cant get in.
I looked at some guide how to reset and set a new root passwd in mysql, im not sure if that worked alright or not. Here's what error i get when tryn to login to phpMyAdmin:
```
Error
#1045 - Access denied for user 'root'@'localhost' (using password: YES)
```

Any ideas?

---

