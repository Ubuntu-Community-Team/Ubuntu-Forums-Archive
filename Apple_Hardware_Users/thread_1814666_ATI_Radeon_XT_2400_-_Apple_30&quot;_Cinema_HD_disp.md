---
title: "ATI Radeon XT 2400 - Apple 30&quot; Cinema HD display - low resolution"
date: 2011-07-29
forum: Apple Hardware Users
---

### Post by manish_jain on 2011-07-29
Hi,

I just started using an (old) Apple 30" Cinema HD display.
However, I have been unable to get beyond the 1280x800 resolution on that.

I have tried searching other forums but everyone seems to suggest that I use a dual-link DVI display. I believe I am already using that. In fact, the cable that I am using is this one: [http://www.google.com/products/catalog?client=ubuntu&channel=fs&q=dual-link+DVI+display+cable&oe=utf-8&um=1&ie=UTF-8&tbm=shop&cid=6633518581110417809&sa=X&ei=-mAzTqHJM-PgiAKlrJ26CA&ved=0CCQQ8wIwAw](http://www.google.com/products/catalog?client=ubuntu&channel=fs&q=dual-link+DVI+display+cable&oe=utf-8&um=1&ie=UTF-8&tbm=shop&cid=6633518581110417809&sa=X&ei=-mAzTqHJM-PgiAKlrJ26CA&ved=0CCQQ8wIwAw)

I am using Ubuntu 11.04, and have both fglrx and ATI drivers installed. However, I must be using fglrx since:
me@mymachine:/etc/X11$ lsmod | grep ati
me@mymachine:/etc/X11$ lsmod | grep fgl
fglrx                2476636  123
me@mymachine:/etc/X11$

I don't know how to switch between drivers. I am also attaching my xorg.conf below.
Any suggestions would be helpful.

Thanks,
Manish

xorg.conf:

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth	24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

---

