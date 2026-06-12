---
title: "How do I install just Xorg + a WM?"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by wr0x2 on 2005-12-20
I want to install just Xorg and TWM. I have done a server install on the computer that I want to put these packages on, and so far I've installed the xserver core and the xserver neomagic driver from apt. What else do I need to install and how do I get everything configured? So far the command "startx" doesn't work.

---

### Post by Dr. Nick on 2005-12-20
do you know the package  name for twm? Try to install it and it should install what it needs. xorg included

---

### Post by wr0x2 on 2005-12-20
Searching for twm or tabbed window manager on the apt cache doesn't return any hits.

---

### Post by wr0x2 on 2005-12-20
OK, I got TWM + deps installed by enabling universe in my sources.list. HTF do I start X? I tried the command X, but when I enter it it returns: "X: cannot stat /etx/X11/X (No such file or directory), aborting."

Same thing when I try to run it with sudo.

---

### Post by ecto on 2005-12-20
Do you happen to have xserver-xorg xbase-clients and x-window-system-core?
I was able to do a server install and have Openbox as my GUI (no gnome, KDE, or XFCE)
[http://www.ubuntuforums.org/showthread.php?t=103806](http://www.ubuntuforums.org/showthread.php?t=103806)

---

