---
title: "ATI problems"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by codeblue315 on 2007-06-29
Everytime I try to install the new driver for my ATI Radeon vid card, I get this error when I try to unpackage the .run file:

Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 165: Syntax error: Bad substitution
Removing temporary directory: fglrx-install


What should I do???

---

### Post by NiBu on 2007-06-29
I estimate you are trying to install the official ati driver from ati.com. 
I would recommend you to install the ati package from the ubuntu repositories:
in terminal : sudo apt-get install xorg-driver-fglrx
Or you can use the new "restricted drivers manager" to install it (Ubuntu Feisty).

The other way to install this driver is to use envy :
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

With envy it is possible to install brand new ati drivers in ubuntu way.

---

