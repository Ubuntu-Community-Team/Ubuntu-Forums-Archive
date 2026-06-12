---
title: "Problem with start up of Openarena"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by shadowforte on 2007-12-19
Every time I go to run it from App's>Games>Openarena it turns to a black screen for a few seconds then goes back to my desktop. Any way to fix this? Or is there antoher way to start the game?

---

### Post by jan quark on 2007-12-19
Try running it through the terminal. Application > Accessories > Terminal. Then type  openarena.

Are you getting any failure reports?

---

### Post by shadowforte on 2007-12-20
It does the same thing. It says:

...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

---

### Post by shadowforte on 2007-12-20
Bump I need some kind of help here guys.

---

### Post by jan quark on 2007-12-20
it seems to be a rendering problem with the openGL 
i am not that experienced but read this, you are not alone
[http://lists.freebsd.org/pipermail/freebsd-questions/2004-January/033229.html](http://lists.freebsd.org/pipermail/freebsd-questions/2004-January/033229.html)
[http://ubuntuforums.org/showthread.php?t=392234](http://ubuntuforums.org/showthread.php?t=392234)
[http://www.linuxquestions.org/questions/linux-hardware-18/debian-installed-nvidia-drivers-could-not-load-opengl-subsystem-332253/](http://www.linuxquestions.org/questions/linux-hardware-18/debian-installed-nvidia-drivers-could-not-load-opengl-subsystem-332253/)

---

### Post by jan quark on 2007-12-20
i found this on this forum, it seems to match your problem
its a driver issue try to follow these instructions
[http://ubuntuforums.org/showthread.php?p=3758154](http://ubuntuforums.org/showthread.php?p=3758154)

---

