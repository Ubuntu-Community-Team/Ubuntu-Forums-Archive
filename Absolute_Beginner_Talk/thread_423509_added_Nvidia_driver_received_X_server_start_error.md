---
title: "added Nvidia driver received X server start error"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by mvilla on 2007-04-25
Installed Ubuntu yesterday and tonight tried to update the NVida drivers from add/remove menu. on restart receiving message:
Failed to start the X server (your graphical inerface. It is likely that it is not setup correctly......

In error messages has the following:
(==) Log File: "/var/log/Xorg.0.log"  Time......
(==) using config file: "/etc/X11/xorg.conf"
(WW) NVIDA: No matching device for insance (Bus ID PCI:5:0:0) found
(EE) No devices deteced.
Fatal server error
No screen found

amdx64 cpu
MSI GeForce 6 NVida NX6200TC PCIe

Everything fine till the driver update. How do I back out or do i have to reinstall. Appreciate any help....

mv

---

### Post by BarfBag on 2007-04-25
If you don't have any data, it's probably easier to reinstall.  You don't have to, though.  Just type the command below and go through the procedure.  It's pretty straight forward.

> sudo dpkg-reconfigure xserver-xorg

---

### Post by mvilla on 2007-04-26
Thanks, reconfigure corrected the issue. Now I'm working on flash and realplayer installs, will probably have new posts tomorow.

rgds,
mike

---

