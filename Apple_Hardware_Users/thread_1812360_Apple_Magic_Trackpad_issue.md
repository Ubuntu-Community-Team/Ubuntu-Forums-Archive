---
title: "Apple Magic Trackpad issue"
date: 2011-07-26
forum: Apple Hardware Users
---

### Post by Michael12uk on 2011-07-26
Hi,

I have a apple magic trackpad which worked until the recent Kernel update. The trackpad is listed as connected under the Bluetooth configuration.

**Threat:**
The mouse cursor doesn't react to any of my movements.

**Little bit regarding my system.**
I use Ubuntu 11.04 with a gnome-shell and KDE-environment.
The Bluetooth dongle seams to working fine.
I am able connect my bluetooth Keyboard and mobile phone. I keyboard input is without any problems.

**Troubleshooting approach till now:**
1.I tried to unpair the Trackpad and repair it, which seams to be working fine.
I tried also to unpair it, restart ubuntu an than pair it agin.
2.I replaced the batteries.


Well I am open to any suggestions

---

### Post by Sef on 2011-07-27
Moved to Apple forum.

---

### Post by johnmurrayvi on 2011-07-28
Same issue here. Tried multiple machines and kernel compilations. To get any movement, it seems you need the module 'hid-magicmouse'. However, it seems to be the final filter any settings in xorg.conf. The module's alias links to the trackpad's pci location and it applies the module's parameters. It made my trackpad into a giant button, with no movement, and only the press-click with one finger working. Although, if you're fine without tap-clicks, if you leave all settings out of xorg.conf, the trackpad has the synaptics driver's gesture configuration and movement does work.

---

### Post by Michael12uk on 2011-07-30
well i tried to remove all the bits in Xorg. it still did not work.
I don't know how to check.. the system inorder to make sure that everything is back to normal.

I removed my entries in /etc/X11/xorg and also in usr/share/X11/ thats all i guess..

---

