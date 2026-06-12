---
title: "Funny colours and black lines in splash, virtual console"
date: 2007-11-18
forum: Apple PPC Users
---

### Post by dougiep on 2007-11-18
Hello

I'm wondering if anyone can help me with a graphical issue:

When I first installed from a Gutsy liveCD, the splash screen came up quite wonky so I used video=ofonly, and all was fine. However, I have been getting the same wonky-ness with the virtual console (Ctrl-Alt-F1/6), and during the shutdown sequence.

For the virtual console, having pressed Ctrl-Alt-F, the screen blanks for about a second, then returns with the same screen, yet with overlaid black lines and no cursor (ie the virtual console background is the same as my normal screen, with black lines). The black lines appear to have some garbled section of the normal desktop.

After a while the image fades, and does a funky little colour changing thing (slowly fades to purple, then blue, then green, then grey... or something of that order).

I don't think the console itself is working either; I tried creating a document on the desktop using nano, but that didnt work... although i was flying blind, so i might have stuffed it up.

Any help would be appreciated.

Comp: running Gutsy PPC
1.6ghz Powerbook G4
512mb ram
ATI mobility 9600 rv350 m10 using "ati driver"
15" screen @ 1280x854

Xorg.conf: (note I have removed the unsupported screen modes from the list, ie. 2150x1024 or whatever it was; still no cigar)

```

...
Section "Device"
	Identifier	"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Boardname	"ati"
	Busid		"PCI:0:16:0"
	Driver		"ati"
	Screen	0
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"Color LCD"
	Vendorname	"Apple"
	Modelname	"Apple Aluminum PowerBook G4"
	Horizsync	30.0-100.0
	Vertrefresh	50-60
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync

	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Monitor		"Color LCD"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	854
		Modes		"1280x854@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"ati"
	Busid		"PCI:0:16:0"
	Driver		"ati"
	Screen	1
	Option		"MergedFB"	"off"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

*I kinda need this to work (the virtual console) so I can do a work-around for the suspend issue I'm still having; in a different thread*

---

