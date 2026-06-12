---
title: "Stoping X Server?"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Hobo Joe on 2007-05-28
I have a simple question, I want to install the beta nVidia drivers, and they say I need to quit the xserver. So my question is, what is the command to quit X and get to a command prompt?

---

### Post by taurus on 2007-05-28
<Ctrl><Alt>F2 and log in with your username and password.  Then, run

```
sudo /etc/init.d/gdm stop
```

---

### Post by Hobo Joe on 2007-05-28
Worked perfectly, thanks a bunch!

On a side note, nVidia has a great graphical installer even without X running.

---

