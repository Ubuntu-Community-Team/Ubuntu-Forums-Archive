---
title: "TwinView Fun..."
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by Icemanyurt on 2007-01-12
I am getting the TV to flash from static to a non-image back to static on boot, here is the relevant parts of my xorg.conf...any help would be great...
> Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nvidia"
	BusID		"PCI:1:5:0"
	Option		"NvAGP" "2"
	Option		"RenderAccel" "0"
	Option		"CursorShadow" "0"
	Option		"Connected Monitor" "crt, tv"
	Option		"NoPowerConnectorCheck"
	Option		"TwinView" "1"
	Option		"MetaModes" "1280x1024,1280x1024; 1280x960,1280x960; 1152x864,1152x864; 800x600,800x600; 1024x768,1024x768; 1280x1024,NULL; 1024x768,NULL"
	Option		"SecondMonitorHorizSync" "28-51"
	Option		"SecondMonitorVertRefresh" "43-60"
	EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
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
Section "ServerLayout"
	Identifier	"TwinView Configuration"
	Screen 0	"Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option 		"Xinerama" "Off"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection



---

### Post by MasterOfDisaster on 2007-01-12
Perhaps moving this thread into the Multimedia section...
That section deals with video drivers in more depth.  Sorry for the lack of help.

---

### Post by Icemanyurt on 2007-01-12
I would agree with you, on principle, but I have gained the most useful help in this forum for this kinda stuff...makes no sense I know...

(and I don't know how to move my threads)

---

