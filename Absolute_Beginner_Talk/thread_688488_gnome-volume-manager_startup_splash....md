---
title: "gnome-volume-manager startup splash..."
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by TrichomeKid on 2008-02-05
I don't know when this "splash" screen started showing up exactly, but it shows up right before the desktop loads (after the bootup splash and login).  I was just wondering if anyone knew how to hide this window.

It says something about "gnome-volume-manager" and has a few small icons... I assume it's mounting my Slave hard drive.  Is there anyway to make this window go away without removing gnome-volume-manager completely?

---

### Post by ptn107 on 2008-02-05
Try going into **System** -> **Preferences** -> **Sessions.**  Under the *startup programs* tab, scroll to find *Volume Manager*.  Click on it, then click *edit* on the right.  The command it runs should be as follows.
```
gnome-volume-manager --sm-disable
```.

---

