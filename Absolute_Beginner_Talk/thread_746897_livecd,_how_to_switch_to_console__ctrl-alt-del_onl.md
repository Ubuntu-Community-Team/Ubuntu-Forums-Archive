---
title: "livecd, how to switch to console ? ctrl-alt-del only drops to logon screen"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by kissson on 2008-04-06
xubuntu 7.1 livecd boot
thx

---

### Post by Hobo Joe on 2008-04-06
I think it's Ctrl-Alt-F1.

---

### Post by kissson on 2008-04-06
ahhh...
but xwindows is still kept on running right?
how to shutdown xwindows and back console?
thx

---

### Post by jordanmthomas on 2008-04-06
> **kissson said:**
> ahhh...
but xwindows is still kept on running right?
how to shutdown xwindows and back console?
thx

from your console:
```
sudo /etc/init.d/gdm stop
```

---

