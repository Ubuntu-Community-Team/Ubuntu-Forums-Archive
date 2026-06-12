---
title: "Problems with Xorg and mouse"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by Ack99 on 2006-10-14
I recently moved my HD to a new computer and, when I booted Ubuntu, Xserver would display an error message. After some searching I discovered that it has something to do with my mouse:
<< core pointer null >>
It isn't the mouse itself and woks fine in my other computer.

---

### Post by bulldog on 2006-10-14
This could be very truth,but you moved your hdd to an other computer with another set of hardware I presume.

Ubuntu is configured for your other set of hardware.
Just putting your hdd in another computer without the right configuration is not a good idea.

You're lucky only your mouse seems to have trouble.

If it's a USB mouse you can try to disconnect and put it in another USB port and see if Ubuntu detects it again.

If it's a PS2 mouse don't disconnect when the computer is turned on!!

It should be better to do a reinstall of Ubuntu,so it detects all your other hardware for proper configuration.

You can try to reconfigure with```
sudo dpkg-reconfigure -phigh  xserver-xorg
``` to see if it detects the mouse.

---

### Post by TheWizzard on 2006-10-14
do a clean install on your new pc. 
if you add your old hdd to the new pc, make sure you have the correct master/slave settings, otherwise you mess things up.

---

