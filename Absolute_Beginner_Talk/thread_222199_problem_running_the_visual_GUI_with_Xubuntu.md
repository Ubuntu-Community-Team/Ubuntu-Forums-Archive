---
title: "problem running the visual GUI with Xubuntu"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by Pablo A Castillo on 2006-07-24
hello again,

I install a xubuntu, but this finish in a shell...!

never start the xserver!! :´(

this says:

Host login: oem
password:


last login mon jul XXXXX...etc  on tty1

oem@host:~$

I type startxfce4  and dont work

how do I to run the xfce gui???

linux is a little bit hard to newbies

---

### Post by aysiu on 2006-07-24
Try these commands in this order: ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
sudo /etc/init.d/gdm start
```

---

