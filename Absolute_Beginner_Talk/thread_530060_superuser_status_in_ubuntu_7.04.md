---
title: "superuser status in ubuntu 7.04"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by raj5045 on 2007-08-20
hi !

can anyone please tell me how to get superuser status in ubuntu 7.04.
i have installed this version and at the time of installation only one password was asked to enter,that is the user password and not the root password.so i don't know how to get into root account.
anyone please help..thanks

---

### Post by heimo on 2007-08-20
> **raj5045 said:**
> hi !

can anyone please tell me how to get superuser status in ubuntu 7.04.
i have installed this version and at the time of installation only one password was asked to enter,that is the user password and not the root password.so i don't know how to get into root account.
anyone please help..thanks

This must be most asked question on these forums. 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by schorsch on 2007-08-20
If you want to run a terminal command as root just type "sudo" in front of it and you will be asked for your (!) password. If you want to run a graphic program as root just type "gksu" under GNOME or "kdesu" when running KDE and it will ask for your (!) password. There is no root account you can change to per default. If you really really have to be root you can switch to it by typing
```
sudo su -
```
and type your password.

---

### Post by raj5045 on 2007-08-20
thanks a lot i got the answer.
great help....................

---

