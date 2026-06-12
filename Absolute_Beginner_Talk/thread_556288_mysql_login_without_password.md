---
title: "mysql login without password ?"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by robb234 on 2007-09-21
hi,

i just installed mysql server 5.0 on my ubuntu feisty. it's a fresh intall and i'm a new user to mysql. 
i wonder if do i really need to type **my mysql -u root -p"** everytime i want to login to mysql ?
just FYI, i'm just a student who want to learn more about sql. 
so is there any way that i can login without having to input the password ?
maybe like just type **mysql** then can run mysql. 
is it possible ? :) :)

---

### Post by hyper_ch on 2007-09-21
you can setup a new user that has no password

---

### Post by robb234 on 2007-09-21
> **hyper_ch said:**
> you can setup a new user that has no password

how to do that ?
i mean the syntax to do that ?

---

### Post by hyper_ch on 2007-09-21
dunno how to do it from the shell, I normally use phpMyAdmin.

---

### Post by LaRoza on 2007-09-21
Look up the "GRANT" command for adding new users, and setting passwords and privileges.

---

### Post by LaRoza on 2007-09-21
> **robb234 said:**
> hi,

i just installed mysql server 5.0 on my ubuntu feisty. it's a fresh intall and i'm a new user to mysql. 
i wonder if do i really need to type **my mysql -u root -p"** everytime i want to login to mysql ?
just FYI, i'm just a student who want to learn more about sql. 
so is there any way that i can login without having to input the password ?
maybe like just type **mysql** then can run mysql. 
is it possible ? :) :)

Create a new user, using the GRANT command, and use this to log on:

```

mysql -u <userName> -p<passWord> <db>

```
You need a user name, you don't need a password, but if you do have it, you can type it after the -p, with no spaces between the p and password. You can also select a database by putting its name at the end.

To log on with just a single word, make a shell script and run it in the terminal.

---

