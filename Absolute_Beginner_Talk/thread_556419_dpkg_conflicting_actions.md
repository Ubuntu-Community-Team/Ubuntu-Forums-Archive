---
title: "dpkg conflicting actions"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by flutti-tutti on 2007-09-21
I have attempted to install Kubuntu 7.04 (Desktop) as a single OS, following the steps outlined on some of the User Guide, and starts almost working, but run into some problems.  One of them is 

After pressing "control-alt-F1", I tried the following command.

sudo dpkg -reconfigure xserver-xorg

I got an error message below.

dpkg: conflictiing actions -e (--control) and -r (--remove)

Any suggestions?
thanks

---

### Post by Bothered on 2007-09-21
The command should be:

```
sudo dpkg-reconfigure xserver-xorg
```

EDIT: That's without a space between dpkg and the -

---

### Post by flutti-tutti on 2007-09-21
Gee, it solved.  thanks a lot.

---

