---
title: "setting up wed server"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by jpates20 on 2008-03-02
I install ,every thing you need to run it, But can't give myself a password 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)can some one help me.........John

apt-get install mysql-server mysql-admin apache2 php5 libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql phpmyadmin

---

### Post by em3raldxiii on 2008-03-03
Something's not right about the way you are trying to install the applications.  First off, you shouldn't be logged in as root, you should be logged in as your own username (assuming you have given yourself super-user privelages).  So you should try this:

```

sudo aptitude install mysql-server mysql-admin apache2 php5 libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql phpmyadmin

```

It will then ask you for your password.  Make sure you type it correctly, and remember that when typing in a password using the console, you will not see the cursor move at all.

I hope this helps :D

---

### Post by Vitamin-Carrot on 2008-03-03
if this is going to be a local server you could get away with lampp

Xampp for windows users.

its an all in one package

mostly recomended for devs
if its going out to the net better to get the actual packages

---

