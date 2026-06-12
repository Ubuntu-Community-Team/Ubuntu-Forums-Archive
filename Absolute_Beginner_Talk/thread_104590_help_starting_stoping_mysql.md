---
title: "help starting stoping mysql"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by pedrotuga on 2005-12-16
how do i star and stop mysql?

---

### Post by lreyes6 on 2005-12-16
in the command line write this
```

/etc/init.d/mysql start - stop - restart

```
one at a time

---

### Post by pedrotuga on 2005-12-16
that path does not exist

but i tryed simply:
```
mysqld stop
```
and it worked
The problem is that i now it doesnt start cause it says that address is already in use.

I think it can be due to i have coment the line

#bind address :127.0.0.1

on 
/etc/mysql/my.cnf

i did that cause i want to have access to the db from other computers not only in the localhost... but now... i cant start mysql :(

what should i do?

---

### Post by lreyes6 on 2005-12-16
just a question... how did you install mysql?

---

### Post by pedrotuga on 2005-12-16
I followed the wiki instructions on the wiki.
I think it was something like

```
sudo apt-get instal mysql
```

---

