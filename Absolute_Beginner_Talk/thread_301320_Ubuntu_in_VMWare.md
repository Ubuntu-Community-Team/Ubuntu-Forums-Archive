---
title: "Ubuntu in VMWare"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by hdgrub on 2006-11-16
Currently I am virtualizing Ubuntu to get a feel for the Linux platform.  I've been using windows for years now and have decided to try something different.  My dilemma, I'm not sure if it is a VMWare related issue or Ubuntu itself.  

VMWare asks to install VMTools to improve various display functions, smooth mouse movement and to synch the clock, etc etc.  I finally figured out the install and got it working except for loosing the scroll wheel ](*,) 

It was working fine before the install.  I'm using a microsoft LaserMouse6000 right now.  Is there a known issue with Ubuntu being virtualized and having hardware problems? 

Thanks in advance for any solution (:

---

### Post by JayTee on 2006-11-17
during the install of Ubuntu did you answer yes or no to using 3 button mouse emulation? This often causes issues whether your running in a VM or not. You could run sudo dpkg-reconfigure xserver-xorg from the terminal in the VM and choose the opposite of what you picked when you first installed.

---

### Post by hdgrub on 2006-11-17
yes that worked.  thanks so much.

---

