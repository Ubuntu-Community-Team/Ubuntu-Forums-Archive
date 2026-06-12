---
title: "lubuntu 12.10 black screen terminal only on mac g5"
date: 2013-03-01
forum: Apple Hardware Users
---

### Post by gusduenas on 2013-03-01
I have the two releases, the desktop and the alternate for lubuntu 12.10 ppc .
I have a g5 1gb ram with:

Chipset Model:	GeForce 6600
  Type:	Display
  Bus:	PCIe
  Slot:	SLOT-1
  PCIe Lane Width:	x16
  VRAM (Total):	256 MB
  Vendor:	NVIDIA (0x10de)
  Device ID:	0x0141
  Revision ID:	0x00a4
  ROM Revision:	2149
  Displays:
**Cinema:**
  Resolution:	1680 x 1050
  Depth:	32-Bit Color
  Core Image:	Hardware Accelerated
  Main Display:	Yes
  Mirror:	Off
  Online:	Yes
  Quartz Extreme:	Supported
  Rotation:	Supported
**Display Connector:**
  Status:	No Display Connected
and 150gb extra hd for lubuntu.
So far after the installation is just terminal no gui...how can I do this? I'd love to have ubuntu installed, but so far nothing happens, any help would be appreciated.

Gus

---

### Post by serpico007 on 2013-03-01
You may look under the minimal cd install option in the Ubuntu website. There were some commands to type to start the download install from Terminal.

---

### Post by str8bs on 2013-03-06
I'm not clear if X is starting or you are just booting to a command prompt.
1. If you did a cli install, did you then "sudo tasksel" and install a desktop? (lubuntu, x.., u...)
2. 6600 has phantom port issues which could cause blank screen Try plugging display in other port or boot: live (or linux) nouveau.tv_disable=1
3. You mentioned no menus in the other thread. Do you mean the GUI is loading but you see no menus? If so, try booting with nouveau.noaccel=1

Check your /var/log/Xorg.0.log for errors that might tell us something. Check the FAQ for more information or known issues. Your card uses nouveau driver.

---

