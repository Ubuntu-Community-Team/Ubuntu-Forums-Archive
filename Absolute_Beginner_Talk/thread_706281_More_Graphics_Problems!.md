---
title: "More Graphics Problems!"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by Dieselguts on 2008-02-24
when i go into system, preferances, appearance, visual effects, it says

The Composite extension is not available

when i want to upgrade the graphic settings. it also says this when i select compiz fusion

---

### Post by glennric on 2008-02-24
I believe to use compiz with an ati video card you will need the package xserver-xgl.
Make sure you have the repo "gutsy universe" installed.

---

### Post by Dieselguts on 2008-02-24
still doesn't stop it saying The Composite extension is not available

oh well

---

### Post by glennric on 2008-02-24
You will have to reboot to start xserver-glx.  If that doesn't work you may also have to change your xserver configuration.  
Look at the file /etc/X11/xorg.conf and see if it has 
```
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```
in it.  If not add it.  You will need root access to do this so type
```
gksu gedit /etc/X11/xorg.conf
```
add the above, save, and exit.  Then reboot.

---

### Post by Dieselguts on 2008-02-24
now it just says Failed to execute child process "compiz" (No such file or directory)

---

### Post by glennric on 2008-02-24
It looks like you don't have compiz installed.  Make sure you have the "gutsy-updates main" or "gutsy-backports main" repos enables (the latter has a newer version), and look in synaptic for compiz.

---

### Post by oedha on 2008-02-24
if you use 7.10....compiz is defaultly installed
can you change the visual effect from none to else ?
(change desktop background - visual effect tab)
maybe you need compizconfig-setting-manager

---

