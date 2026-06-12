---
title: "option to install Ubuntu in windows 7 disappeared"
date: 2011-09-15
forum: Asus Ubuntu Support (CLOSED)
---

### Post by vnt on 2011-09-15
I have netbook eee pc 1005HA and got windows 7 starter installed.

I tried to install Ubuntu 11.04. 
First i ran wubi.exe then I got 3 options to install
1) Demo and full install
2) install in windows (which i can remove)
3) Learn more

I ran option 2 and because I didn't have internet so it failed because it tries to download the .iso.

Then i download the .iso 11.04 and create a USB boot.
I also copied the .iso into the same folder as wubi.exe and ran wubi.exe again. BUT this time option (2) disappeared.

I want option 2 so that i can install Ubuntu in windows.

Please advice.

---

### Post by infinitybot on 2011-09-16
Did you check the MD5 of the iso? You can use daemon Tools to mount the iso and then run Wubi

Check this out too - [https://wiki.ubuntu.com/WubiGuide#How_do_I_install_Wubi_on_a_machine_with_no_Internet_connection.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_install_Wubi_on_a_machine_with_no_Internet_connection.3F)

---

### Post by bcbc on 2011-09-16
Wubi isn't designed to be installed from a USB. Place the ISO and wubi.exe in the same folder on your drive, remove the USB (important), and then run wubi and it will use the one you downloaded. You won't see that boot menu, it will just go to install inside windows.

Part of the problem with the USB is that wubi uses a simple check to stop people installing from a dvd and that's based on the size of the ISO. But with a USB it incorrectly determines that the ISO size = the size of the USB partition. You can force it to install, but then it fails later (unless the usb partition is smaller than the cutoff size).

You can still use the USB as a live USB and later to install if you need to.

---

