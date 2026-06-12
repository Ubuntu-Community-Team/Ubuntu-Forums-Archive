---
title: "Gutsy Upgrade: Newbie with &quot;fatal error&quot;  AHH!"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by aspasia82 on 2007-10-21
Hello everyone!
I'm a relatively new ubuntu user.  I recently installed the Gutsy upgrade.  When it rebooted after install it didn't automatically run the x window system so I typed startx.  This is what I got:

EE Failed to load module i810 (module does not exist, 0)
EE No drivers available.

Fatal Server Error:
no screens found
XIO: fatal IO error 104 on X server...

To tell the truth, I'm lost without the GUI.  Can anyone help me?

I'm running a Dell Insp 1420 laptop with intel integrated graphics chip 9xx
Intel Core 2 Duo T5250, 1.5GHz, 667Mhz, 2M L2 Cache
2GB, DDR2, 667MHz 2 Dimm 
160G 5400RPM SATA Hard Drive

---

### Post by Pumalite on 2007-10-21
Reboot
At the blank screen:
Ctrl+Alt+F1 to get command line
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver. then: startx

---

### Post by aspasia82 on 2007-10-21
thank you thank you 
you are my hero!

---

