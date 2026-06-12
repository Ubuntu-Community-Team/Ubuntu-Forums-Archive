---
title: "compiz-fusion frame-rate problem"
date: 2008-01-16
forum: Apple Intel Users
---

### Post by nikolaos on 2008-01-16
Hi all, i was perfectly using beryl in my feisty distro. i  upgraded to gutsy 2 days ago and followed this guide [http://ubuntuforums.org/showthread.php?t=569654&highlight=xorg.conf+gutsy](http://ubuntuforums.org/showthread.php?t=569654&highlight=xorg.conf+gutsy)
 trying to set up compiz-fusion in my macbook. 
I know that the Graphic card in my MacBook is not an ATI but i couldn't find a guide for mac users anywhere, 
The thing is that when i 
```
sudo apt-get install xserver-xgl
```
compiz starts but my frame rate is awful, i think it has something to do with my xorg.conf file so i am posting the relevant sections.

```
Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option   "XAANo0ffscreenPixmaps"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
```

i hope you can help me.

---

### Post by cyberdork33 on 2008-01-16
remove xsever-xgl as it is only required for ATI (and the older drivers at that).
```
sudo aptitude remove xserver-xgl
```Change your graphics driver to 'Intel' in your xorg.conf:
```
Section "Device"
    Identifier    "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
    Driver        "Intel"
    #Driver        "i810"
    BusID        "PCI:0:2:0"
    Option   "XAANo0ffscreenPixmaps"
EndSection
```

If you still have issues after this, please post your full xorg.conf

---

### Post by nikolaos on 2008-01-19
thank you very much cyberdock33. The problem is now that when i try to enable 
-Normal
-Extra or 
-Custom effects i get a 
"Desktop effects could not be enabled"  message. 
any ideas?

---

### Post by cyberdork33 on 2008-01-20
> **nikolaos said:**
> thank you very much cyberdock33. The problem is now that when i try to enable 
-Normal
-Extra or 
-Custom effects i get a 
"Desktop effects could not be enabled"  message. 
any ideas?Make sure you restart so that the correct drivers are in use, then run 
```
compiz --replace
``` from the terminal. This should give you better output.

---

