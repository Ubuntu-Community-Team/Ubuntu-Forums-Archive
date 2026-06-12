---
title: "X settings for wide monitor"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by bill-linux on 2007-02-23
I have just installed Ubuntu 6.06LTS. I have a Samsung monitor (details below, along with section of xorg.conf) that is 22" wide. I am using a ATI Radeon X1300pro video card. Here is the problem: 

1) Everything is "stretched" on the monitor: Letters, images, etc. A Square image has, roughly, the aspect ratio of the monitor. Is this to be expected? (I've never had a widescreen before.) Is there some setting I should be using?

2) I've tried both the "fglrx" and the ATI drivers. The latter seem to work better, but neither gives me a choice of 1680x1050 resolution. It is listed in the xorg.conf, but when I use Ubuntu's GUI to adjust the screen resolution it only offers 1600x1200. (The monitor often pops up a box complaining that I'm not using optimal resolution!) 

Am I missing something fundamental here?



Samsung 225 BW 22" DVI Widescreen LCD Monitor
# Aspect Ratio: 16:10 (Standard PC Widescreen)
# Resolution: 1680x1050

Here is the relevant section of my xorg.conf file:

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 84.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "vesa"
	BusID       "PCI:4:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. ATI Default Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1680x1050" "1024x768" "800x600" "640x480"
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

---

### Post by tgalati4 on 2007-02-23
sudo dpkg-reconfigure xserver-xorg
control-alt-backspace

If that doesn't work, try substituting "vesa" with "radeon" in xorg.conf.  Save a backup first.
The vesa driver may have an arbitary limit of 1600 by 1200 because that was an insanely large display when it was first written.

---

### Post by bill-linux on 2007-02-26
ISSUES RESOLVED: I was starting x without the monitor attached - I have a KVM switch. When I boot it with the KVM tuned to the booting computer it finds all the right settings. In fact, it look just dandy!

---

### Post by tgalati4 on 2007-02-26
That would do it.  KVM switches are convenient, but Linux cannot guess what your hardware is if it's not connected!  Rule #1 make sure your KVM is connected to your active display.

I'm glad I didn't create a page-long post!

Good luck and share your Ubuntu experience with others.

---

