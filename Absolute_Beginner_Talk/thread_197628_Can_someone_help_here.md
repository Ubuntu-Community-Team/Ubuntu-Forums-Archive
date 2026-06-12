---
title: "Can someone help here?"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-06-16
Hi, 

I have a Fusion HDTV DVB-T card installed and I have downloaded the v4l-dvb file but how do I do the following commands.  I tried typing cd v4l-dvb into the terminal but it said "no such file or directory".  How do you do this?](*,) 

[B]How to build the v4l-dvb kernel modules
The v4l-dvb tree is backwards compatable against recent vanilla kernels. Kernel version 2.6.10 or later is required to build the dvb modules, and version 2.6.12 or later is required to build support for hybrid devices.

   1. Change into the v4l-dvb directory:

      cd v4l-dvb

   2. Build the modules:

      make

   3. Install the modules:

      make install[/B]

Any help appreciated.

Russty

---

### Post by Nikusan on 2006-06-16
A related thread: [http://ubuntuforums.org/showthread.php?t=99647&highlight=dvico](http://ubuntuforums.org/showthread.php?t=99647&highlight=dvico)

---

### Post by Russty of Oz on 2006-06-16
OK I have followed that thread and the terminal did lots of things, but what do I do now?

---

