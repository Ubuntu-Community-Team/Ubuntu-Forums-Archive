---
title: "[SOLVED] Issues with Medibuntu and ndiswrapper"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by kevindubrow on 2007-08-31
Hi, I have a Broadcom 43xx card and configured it with the guide in this link:
[http://ubuntuforums.org/showthread.php?t=405990&highlight=BCM+%24%23xx](http://ubuntuforums.org/showthread.php?t=405990&highlight=BCM+%24%23xx)

That guide worked fine until I got the Medibuntu repository source on my computer and ran an update. I don't remember exactly what the two updates were, but they had "linux-headers" in the names. After the update, I was told to reboot my computer and I did so. When I was loaded up to my desktop again, I noticed that my wireless was acting very odd. I decided I would follow the same Broadcom 43xx guide again, but I ran into a problem and got this error when running the installer:

"Your kernel is not supported by the offline ndiswrapper installer. This is because a DEB hasn't been compiled for your kernel. Please contact the author/maintainer of this software so that one can be included in future versions. Make sure you  specify what version your kernel is. You can out what version it is by opening up a terminal and typing in:  uname -r"

I typed in the code and it told me, 2.6.20-16-386.

I can still see all of my wireless networks, but do not work when I connect to them. I am using an Ethernet cable right now. Does anyone know what I should do to fix this now? Thanks for your time.

---

### Post by kevindubrow on 2007-08-31
Sorry guys, the program had an alternate install specifically for my kernel. So problem solved.

---

### Post by S15_88 on 2007-08-31
can u mark the thread as solved.

thanks, Alain

---

