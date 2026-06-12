---
title: "simple, but frustrating issue"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Lotekx on 2007-06-15
I am trying to get dual monitors to work following this tut:
[http://ubuntuforums.org/showthread.php?t=361124]("http://ubuntuforums.org/showthread.php?t=361124")

When i try to create the svideo dual monitor of the xorg, I get command not found. witness:

sudo /etc/X11/xorg.conf.svideo
sudo: /etc/X11/xorg.conf.svideo: command not found

Why is this??

---

### Post by nylecoj813 on 2007-06-15
> **Lotekx said:**
> I am trying to get dual monitors to work following this tut:
[http://ubuntuforums.org/showthread.php?t=361124]("http://ubuntuforums.org/showthread.php?t=361124")

When i try to create the svideo dual monitor of the xorg, I get command not found. witness:

sudo /etc/X11/xorg.conf.svideo
sudo: /etc/X11/xorg.conf.svideo: command not found

Why is this??

I think it should be 

sudo gedit /etc/X11/xorg.conf.svideo

From what I get from the guide, you are just creating a new xorg.conf file, yes? Well then you probably need to open it in a text editor (gedit)

Let me know if that works!

---

