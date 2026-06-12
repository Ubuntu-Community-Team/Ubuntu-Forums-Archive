---
title: "root password"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by ignazioc on 2006-05-31
hello,
new to linux.
i have installed successfully ubuntu on my thinkpad t40.
during the install i was asked to enter new username which i did.
i am having problems with the root account; during install i was asked to enter new user name but nothing about set up the password for root.
is there a default password for root or did i miss something during the install process?
thanks for your help.

---

### Post by Jagot on 2006-05-31
Read this:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by aysiu on 2006-05-31
You may also want to read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by user1397 on 2006-05-31
Basically, ubuntu is not built for root users.  Instead, you're always a regular user, but you can use the command sudo for root priviliges.  if the command you wanted to type is called foo, and it needs root priviliges, you would type in a terminal:```
sudo foo
```
So by default, you don't know the root password, you're not supposed to know the root password, and you don't need to know it!

---

### Post by ignazioc on 2006-05-31
[QUOTE=Jagot]Read this:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)[/QUOTE]

 1

---

### Post by ignazioc on 2006-05-31
thank you for your help

---

