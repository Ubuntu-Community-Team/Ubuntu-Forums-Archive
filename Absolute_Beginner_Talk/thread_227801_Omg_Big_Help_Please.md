---
title: "Omg Big Help Please"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by Fenix_TigerZ on 2006-08-02
I just tried seting up graphix and now it wont load the linux interface, how can i restore it, im getting a gnome command line, i am extremely desperate.... please help me

---

### Post by T700 on 2006-08-02
> **Fenix_TigerZ said:**
> I just tried seting up graphix and now it wont load the linux interface, how can i restore it, im getting a gnome command line, i am extremely desperate.... please help me

1. Use descriptive titles rather than "HELP" or the like.  More people will look at your problem and try to help.

2.  Please give us some background.  What version of Ubuntu is this?  What EXACTLY did you do/change/configure?  Did you have a GUI before?  What error message are you seeing?

Paul

---

### Post by Fenix_TigerZ on 2006-08-02
The version is 6.06 and i was trying to apply Mobility Radeon 7800 drivers and settings to my laptop so that i could use 3D graphics, something went horribly wrong and now it brings up a terminal where i can login and try to fix the problem, but the prooblem is, this is my first time using ubuntu and am completely clueless on how to fix it....

---

### Post by Perfect Storm on 2006-08-02
In command-line:

sudo nano /etc/X11/xorg.conf

If you remember which changes you made you can reverse them. If that doesn't work try switch to :

 Driver         "vesa"

in Section "Device"


save and exit, reboot

---

