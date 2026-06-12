---
title: "How-to change resolution imac g5 / Edgy"
date: 2006-12-23
forum: Apple PPC Users
---

### Post by manzanares on 2006-12-23
Solution to problem of changing the resolution.
Modify should take place in file /etc/X11/xorg.conf;

step 1: change de HorizSync and VertRefresh
step 2: add your highest resolution

(As with all posts, there are often several solutions to one same problem, and this one works in any case. I believe that is the important things)

Command:

> sudo nano /etc/X11/xorg.conf

and modify according to example below:

(Here is my xorg.conf:)



*******************************
Section "Device"
	Identifier	"NVIDIA Corporation NV34M [GeForce FX Go5200]"
	Driver		"nv"
	BusID		"PCI:240:16:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"

#	HorizSync	28-51
#      change to :
	HorizSync	28-70

#	VertRefresh	43-72
#      change to:
          VertRefresh	43-60

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34M [GeForce FX Go5200]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1024x768" "800x600" "640x480"

# add your max resolution to every line of resolution

	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		 "1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		 "1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		 "1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		 "1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		 "1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
****************************


Good luck.

Manzanares.

---

