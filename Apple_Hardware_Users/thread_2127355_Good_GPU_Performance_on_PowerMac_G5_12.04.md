---
title: "Good GPU Performance on PowerMac G5 12.04"
date: 2013-03-19
forum: Apple Hardware Users
---

### Post by ifirit05 on 2013-03-19
Hey all. I have a PowerMac G5 with a Radeon 9800XT card. I have followed the known issues guide to downgrade my mesa files to 7.11 and tried to pass the radeon.modeset=0 arg to yaboot but I keep falling back to Ubuntu 2D (with horrible window tearing and VERY low glxgears scores). I've tried every yaboot argument out there to get UMS working. Can anyone give me some more advice on this??? Here is my glxinfo (short version):



```


name of display: :0display: :0  screen: 0

direct rendering: Yes

server glx vendor string: SGI

server glx version string: 1.2

client glx vendor string: Mesa Project and SGI

client glx version string: 1.4

GLX version: 1.2

OpenGL vendor string: DRI R300 Project

OpenGL renderer string: Mesa DRI R300 (R350 4E48) AGP 8x PowerPC 64/Altivec TCL

OpenGL version string: 1.5 Mesa 7.11


```

BTW its a PowerMac7,3.

---

