---
title: "Lots of trouble with Radeon X1600"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by pitseleh on 2007-08-11
So I've had no luck with all the fixes for the X-Series Radeon cards I have come across. I started off with running through the guide pinned at the top of this forum concerning X-series cards. No luck.

john@Gooey:~$ sudo apt-get install xorg-driver-fglrx
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xorg-driver-fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

john@Gooey:~$ sudo aticonfig --initial
Found fglrx primary device section
Nothing to do, terminating.

john@Gooey:~$ sudo aticonfig --overlay-type=Xv
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-4

I had no luck there. I tried Envy... no luck. At some point the "Desktop Effects" module stopped working. When I click on it under System-Preferences it says "The Composite extension is not available." I feel like there is no real way of backtracking and that I've kind of permanently screwed up my chances of getting this working without a clean install.

Right now it says:
john@Gooey:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0john@Gooey:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

Is there anything I can do to get this driver working properly?

---

### Post by overdrank on 2007-08-11
> **pitseleh said:**
> So I've had no luck with all the fixes for the X-Series Radeon cards I have come across. I started off with running through the guide pinned at the top of this forum concerning X-series cards. No luck.

john@Gooey:~$ sudo apt-get install xorg-driver-fglrx
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xorg-driver-fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

john@Gooey:~$ sudo aticonfig --initial
Found fglrx primary device section
Nothing to do, terminating.

john@Gooey:~$ sudo aticonfig --overlay-type=Xv
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-4

I had no luck there. I tried Envy... no luck. At some point the "Desktop Effects" module stopped working. When I click on it under System-Preferences it says "The Composite extension is not available." I feel like there is no real way of backtracking and that I've kind of permanently screwed up my chances of getting this working without a clean install.

Right now it says:
john@Gooey:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0john@Gooey:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

Is there anything I can do to get this driver working properly?

HI have you seen this thread it has helped
[http://ubuntuforums.org/showthread.php?t=488385&highlight=X1600](http://ubuntuforums.org/showthread.php?t=488385&highlight=X1600)
Good luck

---

