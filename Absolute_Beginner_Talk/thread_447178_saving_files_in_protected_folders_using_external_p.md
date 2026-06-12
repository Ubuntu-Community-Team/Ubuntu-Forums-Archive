---
title: "saving files in protected folders using external programs"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by ThePolemistis on 2007-05-17
HI

I want to use BlueFish to save to /var/www directly. Unfortuanetly u need root permissions.

How am I supposed to do it through BlueFish like I do in terminal using sudo?

Thanks

---

### Post by FuturePast on 2007-05-17
/var/www should have a group of www or similar. Add yourself to that group:
$ sudo adduser me www

logout and login again, and make sure that the group write permission is set on the dir:
$ sudo chmod -R g+w /var/www

---

