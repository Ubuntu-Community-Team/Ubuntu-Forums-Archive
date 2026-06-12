---
title: "Need to reset monitor settings"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by Lee7 on 2007-10-21
Hi all,

I was messing around trying to sort of my dual display, but now when rebooting Ubuntu doesn't detect the right display settings for my primary display. I can use recovery mode to type in a command to reset this display settings, but I need to know what that command is.

Any help is appreciated.

---

### Post by mikeyphi on 2007-10-21
If you're on Gutsy - open the Screens & Graphics GUI and select your correct monitor or similar then set resolution.

---

### Post by Meson on 2007-10-21
I found that the Screen and Graphics GUI doesn't work very well.  Here is my xorg.conf file.  I've kept it at general as possible, however the one thing that is specific is that I'm using an nvidia card and some of the options are nvidia specific.

```
Section "Files"
EndSection

Section "Module"
	Load	"glx"
	Load	"dbe"	
	Load	"extmod"
	SubSection "extmod" Option "omit xfree68-dga" EndSubSection
	Load	"type1"
	Load	"freetype"
EndSection

#I've omitted the Input Devices to save space

Section "Device"
	Identifier	"device0"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"TwinView" "true"
	Option		"ConnectedMonitor" "DFP-1, CRT-1"
	Option 		"TwinViewXineramaInfoOrder" "DFP-1, CRT-1"
	Option		"TwinViewOrientation" "leftOf"
	Option		"MetaModes" "nvidia-auto-detect, nvidia-auto-detect"
	Option		"RenderAccel" "true"
	Option		"UseEdidDpi" "true"
	Option		"DPMS" "true"
EndSection
Section "Monitor"
	Identifier	"monitor0"
	Option		"DPMS"
EndSection
Section "Screen"
	Identifier	"screen0"
	Device		"device0"
	Monitor		"monitor0"
	DefaultDepth	24
	SubSection "Display"
		Modes	"nvidia-auto-detect"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option		"Xinerama" "false"
EndSection
```

I found that for all of the Mode entries that "nvidia-auto-detect" works just fine.  The real important stuff here is```
	Option		"TwinView" "true"
	Option		"ConnectedMonitor" "DFP-1, CRT-1"
	Option 		"TwinViewXineramaInfoOrder" "DFP-1, CRT-1"
	Option		"TwinViewOrientation" "leftOf"
```

Line 1 obviously enables TwinView.
Line 2 gives exactly which monitors are connected.  I found that this was the most difficult thing to figure out.  Instead of two monitors, try to connect one at a time.  Cycle through CRT-0-1-2-etc and DFP-0-1-2-etc, see what happens.  Everything is much easier when you know exactly how your monitors are identified by the system.  Note that all VGA monitors are CRT, and DVI monitors are DFP.  It took me a while to figure that my laptops built in screen was CRT-1
Line 3 lets you specify the order that he monitors are seen.  This line was necessary for me to get the login screen on the correct monitor.
Line 4 Specifies the orientation of the two monitors.

---

### Post by LeeAdkins on 2007-10-21
If you are looking for the command line Xserver config wizard, I used
sudo dpkg-reconfigure xserver-xorg
after messing with dual screens on my laptop, because it royally messed up my xorg.conf file.  The wizard was much easier than trying to edit my conf file, but this just fixed my laptop's display: it still didn't fix my second display. I may look into the info Meson has provided to work on that later.

---

