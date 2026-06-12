---
title: "MySQL: root cant add new database! help!"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by d0rr on 2006-04-29
I am currently setting up LAMP in my Ubuntu (am new in Linux)..

I have done everything from setting up apache, configuring php, installing mysql up to having phpmyadmin in my server. 

However, I could not add new database within phpmyadmin.. the same goes to terminal, when I logged into root of mysql (mysql -u root -p)

I am helpless now, been trying for hours   :stars: 

Your assistance is highly appreciated!~   :respect:


**Extra Details:**

I receive the following error. I believe I have not logged into root of mysql, but how do I do that? It isnt the same thing as *mysql -u root -p* right? 

```
root@xxx:~ # mysqladmin create test_db
mysqladmin: CREATE DATABASE failed; error: 'Access denied for user: '@localhost' to database 'test_db''
```

My mysql root password is set to be blank (empty). How could I set the root  password? When I tried to edit the password, the following message appeared:

```
root@xxx:~ # mysqladmin password xxxxx
mysqladmin: unable to change password; error: 'Access denied for user: '@localhost' to database 'mysql''
```

---

### Post by hw-tph on 2006-04-30
**mysqladmin -u root -p password** will let you set a new password for root in mysql. Note that you do not need to run a root terminal, just run mysql/mysqladmin with "-u root".

"Access denied for user: '@localhost'" seems to indicate that mysql doesn't get what user you want to run as so use -u all the time. Then you'll know who you run as. So **mysqladmin -u root -p create test_db** should let you create a test db.


Håkan

---

