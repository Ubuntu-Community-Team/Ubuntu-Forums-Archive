---
title: "Display trouble in KDE"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by Darklighter137 on 2007-03-08
Hi!  When I select to boot from Ubuntu in GRUB (or just after the system shuts down from Linux), my monitor flashes an "Input signal out of range error".  I have an ATI Radeon Xpress 200 card (the problem was occurring before I installed the drivers). 

Please also note that I installed my system with the alternate CD.  Is this a hazard to my monitor?  How can it be fixed?

---

### Post by igknighted on 2007-03-08
You just need to install the ATI drivers, see this thread, I just posted some instructions.  You will need to start in recovery mode, it will be CLI only, but type the commands and install the drivers and when you start normally the GUI should come up fine.

[http://www.ubuntuforums.org/showthread.php?t=379653](http://www.ubuntuforums.org/showthread.php?t=379653)

---

### Post by Darklighter137 on 2007-03-08
Thank you, but I've already installed the drivers and the problem persists (they do work though, because my correct resolutions were enabled on reboot).  I've installed Ubuntu before, along with the drivers, and this error has never occured.

---

### Post by Darklighter137 on 2007-03-08
I read through your post, and that was the exact thing that I did to install the drivers.  Yet, when I type glxinfo | grep direct, I get a "no" and some stuff about "mesa". x.x

---

### Post by Darklighter137 on 2007-03-09
Bump

---

### Post by igknighted on 2007-03-09
It's issues like this that make ppl hate ATI.  Technically what you did should work fine, but for some reason the kernel module doesn't want to load.  Try google searching the "envy script", uninstalling your current ati drivers, then reinstalling via Envy.  You might have better luck.

---

