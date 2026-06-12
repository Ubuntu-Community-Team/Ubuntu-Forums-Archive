---
title: "Problem While Booting"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by kost on 2007-08-07
I had a problem during the installation from CD when pressing Start and Install option (Kernel 2 lines were loading but after a while my screen was black and after a that my monitor was turning off) and I fixed it by pressing F6 and then erasing the command Quite Splash and adding vga=ask and then selecting 80x25 i thing. But when i get in the very first page when I start my PC I am in a place which asks me to select what OS I would like to use. I go to the first and "e" then to the second row and I press "e" again and I erase the quite splash etc  but when I boot it I get an error that it cant show me my graphical interface or something and it asks me to press yes or no. Anyway, then its something like MS-DOS command line and it asks for my username and password. Any ideas please?

Thanks in advance,


kost

---

### Post by Rocket2DMn on 2007-08-07
OK, so you wound up at a terminal since the X-server (GUI) couldn't start - login with your username and password as it asks.  Let's try reconfiguring your X-server - the following command will take you through a setup process which asks you questions about your hardware.  You should read it, not just ENTER your way through in a hurry.  Enter your password when prompted.
```
sudo dpkg-reconfigure xserver-xorg
```Use TAB to move around and SPACEBAR to select/enable.
Eventually you will be asked about your video driver and screen resolutions.  If you have an Nvidia card, select nv for the driver and if you have an ATI card, select ati.  On the screen resolutions page, enabled your monitor's highest resolution and everything less.  After the configuration is complete, you can start GNOME display manager:
```
sudo /etc/init.d/gdm start
```
If for some reason that doesn't work, try
```
startx
```
You should have the GUI now.

---

### Post by kost on 2007-08-07
Okay Thanks a lot, I will let you know.

---

