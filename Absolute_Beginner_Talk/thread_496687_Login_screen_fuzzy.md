---
title: "Login screen fuzzy"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by bcdeck on 2007-07-09
I've read through the threads on screen resolution that I can find, but I haven't been able to fix my issue. Any help would be greatly appreciated.

My login screen is blurry -- it looks like it's vibrating up and down very slightly. After login everything looks fine. 

I'm on Feisty 7.04, and here's my xorg.conf file:


EDITED

---

### Post by FleetAdmiral74 on 2007-07-09
In administration - login window, if you change the theme (say, plain) does it still have the same fuzziness?

---

### Post by bcdeck on 2007-07-09
Yes it does.

---

### Post by bcdeck on 2007-07-17
A possible solution of sorts: I noticed that by turning off the Show Actions menu, I no longer have the option to shut down -- I only can hibernate. Everything is clear when logging back in after hibernation.

In hibernation, the machine seems just as "off" as it is when I shut down. So .......

-- I'm running Feisty 7.04 on a desktop
-- I'm the only one using the machine
-- Ubuntu is the only OS on the machine
-- "Restart the Xserver with each login" is checked in my login options.
-- Everything works fine when loging back in after hibernation.

 Will I run into problems if I only hibernate and don't shut down?

---

### Post by bcdeck on 2007-07-18
After reading through various threads, I've tried the following:

-- Ran the dpkg-reconfigure xserver-xorg utility. It crashed out midway through and resolution went to hell. Restored xorg from a backup and was o.k. again, but still fuzzy at login.

-- Edited xorg down to just the resolution I want. Still fuzzy at login. Tried broadening the range of horizontal sync and vertical refresh. Still fuzzy. Tried lowering default depth to 16 from 24. Still fuzzy.

I'm getting really good at editing xorg and restoring it if I screw something up, but I'm no closer to fixing my problem. Anyone have any ideas?

I'm on Feisty 7.04, and here's my current xorg:

Section "Monitor"
	Identifier   "Gateway fpd2275w"
	HorizSync    64.7 - 64.8
	VertRefresh  59.9 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI RADEON X800"
	Driver      "vesa"
	Option	    "UseFBDev" "true"
	BusID       "PCI:3:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Gateway fpd2275w"
	Device     "ATI RADEON X800"
	Monitor    "Gateway fpd2275w"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1680x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

---

