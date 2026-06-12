---
title: "There is no apt-get , opkg or yum"
date: 2014-04-22
forum: Any Other OS
---

### Post by umtkyck on 2014-04-22
Hi,

I bought a Exynos4412 board from China , they gave me a linux distribution and there is only busybox in it and I can not install anything (there is no apt-get, opkg,yum).I tried wget it worked but any compliler(gcc) in this distribution.I dont know how to add apt-get or yum to OS.Please help me.

---

### Post by PondPuppy on 2014-04-22
If I understand right, Exynos 4412 uses an ARM processor. The board might have been shipped with Android as an operating system, or maybe (as Odroid Hardkernel?) with Xubuntu. What is the specific Linux distribution on the machine?

---

### Post by umtkyck on 2014-04-22
On board iTOP4412 (Arm Cortex A9 Quad Core ) came with Android . They also sent a cd , there is two image in it android and linux+qt , I loaded linux+qt to board and Qtopia screen appeared. Then , I tried to install openssh from web but there is no apt-get or opkg.

How can I install apt-get or opkg ?

---

### Post by PondPuppy on 2014-04-22
I can't help much. Qtopia was a Linux distro for embedded systems. I suspect it does not support apt, yum, or rpm. It appears that Qtopia became Qt Extended, and then development stopped in 2009. A fork of the project is called Qt Extended Improved. Check [http://wiki.openmoko.org/wiki/Qt_Extended_Improved](http://wiki.openmoko.org/wiki/Qt_Extended_Improved) if you haven't already, there may be some info there you can use. Perhaps you can install a Debian for ARM on the board, don't know. I hope someone has better advice for you.

---

