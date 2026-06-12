---
title: "Video Card"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by mumebuhi on 2006-10-10
Where can we find out about the installed driver for the video card? In Linux, how do we install a new video card driver? 'apt-get install'? 

Thank you.


Buhi

---

### Post by CatKiller on 2006-10-10
If you look at your /etc/X11/xorg.conf file ```
less /etc/X11/xorg.conf
``` and scroll down to your Device section, it will tell you which driver you are using.

If you've installed your driver package with Synaptic, then you'll get updates to the driver in the same way that you get updates to any other software.

---

### Post by mumebuhi on 2006-10-10
The device section says:
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

However, when I searched for 'ati' in Synaptic Package Manager, the package is not there. Help?

---

### Post by CatKiller on 2006-10-10
That driver is included in the xserver-xorg-driver-ati package.

---

