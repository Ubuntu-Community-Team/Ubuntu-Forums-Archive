---
title: "ATI Radeon 3D Acceleration Problem"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by JBen on 2007-03-04
I am having trouble running 3D games with 3D acceleration enabled. I have the latest ATI drivers installed, but when I try and run a game, I get what seems like 1 FPS. I have a ATI Radeon 9600 Pro card.








Thank you!

---

### Post by Regel on 2007-03-04
What does```
fglrxinfo
``` say?

---

### Post by JBen on 2007-03-04
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

---

### Post by JBen on 2007-03-04
I went to the Mesa website and downloaded the newest files, but I have no clue what I'm doing.

---

### Post by JBen on 2007-03-04
Shameless bump :redface:

---

### Post by ed-j on 2007-03-04
Hi !

Could you please tell me which version of Ubuntu you are using?

---

### Post by jimrz on 2007-03-04
> **JBen said:**
> display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

looks like you do not have the "fglrx" drivr properly installed/configured. search these forums for "mesa" and you will find lots of threads that may or may not get you going. however if your 9600 pro is like the 9600 mobility 128 Mb on my laptop, it is not supported for 3d acceleration by the proprietary fglrx driver. since the "ati" driver from restricted modules that the intitial install likey used for your card does provide some hardware acceleration (glxgears -printfps shows about 1900 w/ gears window active and about 6000 with it covered by the terminal window) on mine, you would actually lose functionality by going with the "fglrx" (with or without the 'mesa issue'). if this is the case, i would restore your original /etc/X11/xorg.conf (i hope you did back it up), entirely remove the "fglrx"  and go with the 'ati' driver, as this will  likely provide the best performance available.

---

