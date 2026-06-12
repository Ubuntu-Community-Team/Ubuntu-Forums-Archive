---
title: "XServer Failure"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by bobbyaa on 2006-04-29
When I try to start up ubuntu, I get:

failed to start the xserver (your graphical interface)
(EE) No devices detected.
Fatal Server Error:
no screens found

I have checked the xorg.conf and it lists this in the section pertaining to the video:  

Section "Device"
	Identifier	"GeForce 7900GT"
	Driver		"nv"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"GeForce 7900GT"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection


Any ideas?

---

### Post by olsonar on 2006-04-29
Try running this from the command prompt:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by bobbyaa on 2006-04-29
What does that command do?  I have to result to doing everything in command line.  I can't even get "links" to work to do the downloads.

---

### Post by olsonar on 2006-04-29
It automatically reconfigures your xserver. and to get files from the net while at a command prompt, use 

```
wget *URL_of_file*
```

---

