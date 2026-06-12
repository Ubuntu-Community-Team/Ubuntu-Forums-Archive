---
title: "help me fix my xorg.conf"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by jaynyls on 2007-04-13
hey all,

i tried putting beryl on ubuntu 7.04 by following some tutorial.  unfortunately, something called X server won't work and i can't get a GUI. Instead, I'm dumped to a DOS-like prompt.  i'm trying to gedit my xorg.conf file to change the offending setting but i keep getting "cannot open display:"...some help?!

---

### Post by solracarevir on 2007-04-13
The DOS-like prompt you said is called the terminal, type this on your terminal 
```
[SIZE=-1]sudo dpkg-**reconfigure xserver**-xorg"[/SIZE]
```
it will askyou for your password, and then you will start the process fo reconfiguring your xserver (Xserver is on charge of controlling your display)
hope this would help

---

