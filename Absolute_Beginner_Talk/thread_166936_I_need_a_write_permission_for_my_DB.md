---
title: "I need a write permission for my DB"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by Isoss on 2006-04-27
I was trying to manage my database through phpmyadmin ... I can't change, or drop or do anything without permission as a root! how can I get a write permission? and how can I obtain this permission by defualt?

Thanks

---

### Post by Isoss on 2006-04-27
Hello ... Please, somebody help!

---

### Post by mostwanted on 2006-04-27
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

edit: now that I think about it, it would probably be different using a web interface. Forget it.

---

### Post by Isoss on 2006-04-27
[QUOTE=mostwanted][https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

edit: now that I think about it, it would probably be different using a web interface. Forget it.[/QUOTE]

Yeah, I really can't find anything about my situation in the page that you suggested ... I get really upset when I don't have access into stuff easily ... ](*,) 

Why there's too much restriction in ubuntu?

---

### Post by cgjones on 2006-04-27
What kind of root permission do you need? Root on the computer, or root on the database? And before you blame Ubuntu for being too restrictive, this is straight off phpMyAdmin's page.
> 
phpMyAdmin can manage a whole MySQL server **(needs a super-user)** as well as a single database. To accomplish the latter you'll need a properly set up MySQL user who can read/write only the desired database. It's up to you to look up the appropriate part in the MySQL manual.


---

### Post by Isoss on 2006-04-28
Ok ... first .. I need root permission on Database (working with PHPMYADMIN) ... I can't inset, or delete, or update or do anything with it. searching in the manual is a big loop cuz I am still a rookie in linux and all i know concerning mysql is how to set the user and password. and I've set them as user="root" and password = "" ... I have read access but I don't have write access ... WHY? somebody please help! this is taking time and I have work to do ... so any ASAP help will be appriciated.

---

### Post by Isoss on 2006-04-28
Let me show you the error that PHPMYADMIN is giving me:

```

Error

SQL query:

UPDATE `svd` SET cid = '22' WHERE bid = '66' AND cid = '23'

MySQL said: Documentation
#1036 - Table 'svd' is read only 

```

notice that table is read only! I need a write permission .. it asks me when loging in phpmyadmin for logins and I simply enter the root logins that I have set in terminal:
```
sudo mysqladmin -u root password ""
```

---

### Post by indytim on 2006-04-28
I'm remote now so I can't check my box running Ubuntu.  Let me offer this as something to check out.  Make sure that you have full permission on the folder containing phpMyAdmin.  When I set up LAMP on one of my boxes running Ubuntu, I had to change the permissions on the root folder for the Apache web server.  As I said, I'm remote and can't give you specifics but if this is the problem, perhaps someone else from the collective can chime in with the fix on the folder permissions (if that's the root of your dilema).

Regards,

IndyTim

---

### Post by Isoss on 2006-04-28
alright ... if you mean /var/www/ , I've just checked it and apparently, I don't have write permission ... that's another thing I need to solve ... so how can I obtain permission to any folder? and I need permission by defualt ... Thanks.

---

### Post by cgjones on 2006-04-28
To set the initial password, you would do the following:
```

mysqladmin -u root password *newpassword*

```
To log in once a password has been set, do the following:
```

mysqladmin -u root -p

```
This will prompt you for the password that you set initially. I'm not positive if you need to use sudo for either one of these commands, so try it both ways.

As for the specific error, I'm not familar with phpMyAdmin. One thing you could try is to reload the grant tables.

---

### Post by Isoss on 2006-05-01
Does anybody know how to get permission to /var/www/ ?
Please help

---

### Post by Isoss on 2006-05-01
Hey ... I noticed something wierd! I copied the mysql data from windows files to /var/lib/mysql folder which contains the mysql DBs ... when I edit "the default" mysql DBs or insert or do anything it works. but when I try to work with the DBs that I have copied into that folder it tells me that the tables are "read only" ... does that make someone suggest something here?

Please help me ... this holds up my work! I can't waste more time on this ... so please help.

---

### Post by annda on 2006-05-01
if you want to be able to write to the whole directory type in the terminal:

```
sudo chmod 777 -R /var/www
```

this recursively sets read+write+execute priviledges to all users.
check out this link:
[https://wiki.ubuntu.com/FilePermissions](https://wiki.ubuntu.com/FilePermissions)

however, this can be dangerous when you go online with the server - anyone can mess with your files.

---

### Post by Isoss on 2006-05-01
Thanks you very much. But what about MYSQL BDs?

---

### Post by annda on 2006-05-01
if you have the problem only with the DBs copied from win, make sure you have no writing restrictions on those file.

otherwise check the mysql DB and make sure you have all the privileges (especially table users, but maybe also db or tables_priv, it depends on your version of phpMA).

good luck and keep posting.

---

### Post by Isoss on 2006-05-01
Hey ... I found the solution. Please go read this post:
[http://ubuntuforums.org/showthread.php?p=975110](http://ubuntuforums.org/showthread.php?p=975110)

---

