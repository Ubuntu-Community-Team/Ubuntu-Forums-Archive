---
title: "Can't get my Onboard X200 driver installed.."
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by Thorin129 on 2007-09-15
I have Ubuntu Feisty, and my Radeon X200M will not install correctly..  It wont let me use the desktop enhanced graphics...   

Keeps giving me this msg when i try to create the deb packages to install..

baller123@baller123:~/Desktop$ sudo sh ati-driver-installer-8.26.18-x86.run
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.26.18..................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 163: Syntax error: Bad substitution
Removing temporary directory: fglrx-install


I also need help installing games with Wine...I thought it would create a visual desktop of Windows, and run the game through that?

---

### Post by alienexplorers on 2007-09-15
have you tried using the ENVY script

> [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Thorin129 on 2007-09-15
it worked, but now When I go to Desktop Effects it says The Composite Extension is not available.  What exactly does that mean?

---

### Post by alienexplorers on 2007-09-15
I believe you have to add a option for composite in your xorg.conf file.  Not sure how to go about this on a ati card.

---

