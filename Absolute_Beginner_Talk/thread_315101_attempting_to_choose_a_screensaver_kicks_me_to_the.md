---
title: "attempting to choose a screensaver kicks me to the login screen"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by bcdeck on 2006-12-08
EDIT: Problem solved, it looks like -- I'm leaving the post in case others have the same issue.


I'm running Edgy on a machine with an ATI Radeon X800 All-in-Wonder card (AGP), and when I try to browse through screensavers I get kicked out to the log-in screen.

When I log back in, the last screensaver I clicked on is selected and runs fine, but if I try to choose a different one I get kicked back out. To check if it's an opengl thing I added the game Billard-GL, and that runs fine.

I'm stumped on this -- perhaps it's a driver issue? 

My fglrxinfo info is:

display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 AGP 1x TCL
OpenGL version string: 1.2 (1.3 Mesa 6.5.1)

EDIT: I ran through the steps at [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI), and now things are stable. My fglrxinfo now gives me this:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

---

