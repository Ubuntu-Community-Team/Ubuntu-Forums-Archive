---
title: "External Monitor on a MacBook: Cannot use native resolution"
date: 2007-03-22
forum: Apple Intel Users
---

### Post by Mipsel on 2007-03-22
Hi everyone, 

today I bought a Siemens Fujitsu Scaleoview L22-1W which uses a native resolution of 1680x1050. 
h-freq 30-82
refresh rate 50 75
maximum pixel rate 150MHZ


So far I got cloning and everything else to work, like I wanted. Expect that I cannot run the external monitor with the resolution if 1680x1050.  I have tried a lot of things: several different modlines.... 

But nothing helps, currently it runs on 1280x800 which sucks on a 22'' monitor. 

I have attached my xorg.conf and my xorg.log. Maybe somebdoy knows where the problem is.

Thanks a lot for any support. The birthday kid wants to play with his present :( 
[http://batland,de/xorg.conf]("http://batland.de/xorg")
[http://batland.de/Xorg.0.log]("http://batland.de/Xorg.0.log")
Bye, 
Mips

---

### Post by cyberdork33 on 2007-03-22
From the log:
```

(WW) I810(0): config file hsync range 28-64kHz not within DDC hsync range 30-82kHz
(WW) I810(0): config file vrefresh range 43-60Hz not within DDC vrefresh range 56-76Hz
```

Maybe this is the issue? It looks like your two Monitors are getting crossed in the config somehow.

---

### Post by pxwpxw on 2007-03-23
> **Mipsel said:**
> 

 currently it runs on 1280x800 which sucks on a 22'' monitor. 

I have attached my xorg.conf and my xorg.log. Maybe somebdoy knows where the problem is.



Possibly here in the log:

> ) Primary Device is: PCI 00:02:0
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found

X found 2 devices but xorg.conf has nothing for BusID PCI:0:2:1

xorg.conf has both BusID same:

> Section "Device"
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"i810"
	Screen 0
	BusID		"PCI:0:2:0"
	Option "MonitorLayout" "CRT,LFP"
	Option  "XAANoOffscreenPixmaps"
EndSection

Section "Device"
	Identifier 	"Intel"
	Screen 1
	Driver		"i810"
	Option "MonitorLayout" "CRT,LFP"
	BusID		"PCI:0:2:0"
EndSection


Change one of them to BusID PCI:0:2:1
Then X will recognise both and the ModeLine should be unnecessary.

the log again:

> (II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) I810(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) I810(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) I810(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 82 kHz, PixClock max 150 MHz
(II) I810(0): Monitor name: L22-1W
(II) I810(0): Serial No: YEQX011703

Xorg  has a mode for  1680x1050.
==========

---

### Post by david_edmundson on 2007-03-23
I'm fairly sure you're right in have the PCI Bus ID to be the same, it is in my config file.

You may want to look at the results of ddsinfo/ddcinfo/ddsprobe/ddcprobe (it's one of them..type dd and press tab a lot) This shows the information from the monitor.

Also try turning clone off. Clone may be getting confused over 2 different monitors resolutions.

---

