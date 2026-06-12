---
title: "3D games running tooooo slowwww! HELP!"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by Devezu on 2007-07-04
Sorry for being a noob, but for some strange reason, 3d games such as assault cube and gridwars run too slow. my computer is not _that_ old to be running games like that. please help. my video card is an ati radeon x300

---

### Post by reynal_sf on 2007-07-04
Do you have the driver for the Video Card installed?

---

### Post by bobplano on 2007-07-04
do you have fglrx? if so post your fglrxinfo here

---

### Post by Devezu on 2007-07-04
ok. Here's the new dilema. the 3d games run really fine when i have the restricted drivers installed, but beryl doesnt. when i disable it, beryl runs and the games dont. is there some way to have both working at the same time?!?!?! HELP!!!!!!!!!!!

---

### Post by Devezu on 2007-07-04
my fglrxinfo is:

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X300/X550/X1050 Series
OpenGL version string: 2.0.6334 (8.34.8)

beryl outputs:

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension



does it help?

---

### Post by dfreer on 2007-07-04
Problem with ATI drivers:
when using the open-source radeon driver, 3D acceleration may not work but AIGLX (needed to run beryl without a seperate X session) will.
When using the official ati fglrx driver, 3D acceleration may work but AIGLX is not always supported, so in order to use beryl you will have to launch a seperate XGL session. You will most likely not be able to run Beryl and 3D games at the same time, although you could switch back and forth between the two sessions.

EDIT: although this doesn't seem to be the case with the info you just provided, you might be able to run AIGLX with the fglrx driver.
You might want to try adding to the end of the /etc/X11/xorg.conf file (back it up first):
```
Section "Extensions"
        Option         "Composite"   "Enable"
EndSection 
```
Although someone with more ATI experience might be able to help you more, I'm a nvidia guy myself.

---

### Post by Devezu on 2007-07-04
I am very sorry, but that suggestion made it worse (no window manager!). But i was able to fix it

---

