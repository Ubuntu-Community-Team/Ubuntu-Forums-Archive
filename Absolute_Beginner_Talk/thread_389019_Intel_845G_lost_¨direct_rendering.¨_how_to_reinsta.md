---
title: "Intel 845G lost ¨direct rendering.¨ how to reinstall driver?"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by killbill on 2007-03-20
I used to have direct rendering on my Intel 845G Video card. but somehow, now I´e got these( and my driver is still i810):
I´ve tried the one from intel.com, but no use. **Can I get back the previous driver shipped with ubuntu?**
==========================================
~$ glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

==========================================

$ glxgears
X connection to :0.0 broken (explicit kill or server shutdown).
========================================


Please help me, guys!

---

### Post by denver on 2007-03-20
try the following:

> apt-get install xserver-xorg-video-i810

OR


> apt-get install xserver-xorg-video-intel

and see if that does the trick

---

### Post by glennric on 2007-05-07
Did you ever get this to work.  I have an 845G integrated graphics card and I have the same problem.  No direct rendering.  I have the xserver-xorg-video-i810 driver installed.

---

