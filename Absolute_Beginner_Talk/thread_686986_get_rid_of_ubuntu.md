---
title: "get rid of ubuntu"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by kevmore on 2008-02-03
I installed Ubuntu.  It was cool.  Then I installed Kubuntu.  It was cooler.  I want to keep Kubuntu and punt Ubuntu.  How do I do that??

---

### Post by NightwishFan on 2008-02-03
If you mean the desktop manager:
You can leave it installed and just set up kde as default.
If you truly want to bother to remove it i believe the command is:

sudo apt-get remove gnome-desktop


If you mean you dual booted ubuntu and kubuntu:
Look for gnome partition manager in add/remove or synaptic and delete the ubuntu partition.

---

### Post by PaulSipot on 2008-02-03
Have you installed both of them and dual booting? or installed KDE over a gnome based ubuntu?

---

### Post by Majorix on 2008-02-03
> **NightwishFan said:**
> If you truly want to bother to remove it i believe the command is:

sudo apt-get remove gnome-desktop

The correct command goes
```
sudo apt-get remove --purge ubuntu-desktop
```

---

### Post by kevmore on 2008-02-03
I installed kde over a gnome ubuntu

---

### Post by Majorix on 2008-02-03
Then try running the command in my first post and report back!

---

### Post by kevmore on 2008-02-03
Well, maybe I'll do what nightwish suggested, and just boot the one i want.  
But I am going to start a collection of code and paste them to my tomboy notes.  That way I can use it when I want.  Thanks Everybody.

---

