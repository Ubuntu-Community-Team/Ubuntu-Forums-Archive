---
title: "Using MonitorsDB in hwdata (another resolution thread)"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by SupraBlur on 2008-03-04
So life was peachy with my old Dell 20" widescreen monitor, running 1680x1050 with no problems when I decided to upgrade to the Dell 2208wfp (22" widescreen).  The native resolution is the same as the 20, so I figured it should be plug and play.  No such luck.

I've followed the numerous resolution-related threads, and have had no luck, even after manually editing xorg.conf to support the resolution, pasting the results from CTV, etc.  I did manage to run into the Fedora GIT that's supported by Dell, whose MonitorsDB file includes my model.  Being a complete n00b, though, I have no idea what to do with it.  I installed hwdata from the repositories, which created the /usr/share/hwdata/ folder, and I've overwritten the existing MonitorsDB with the one I've downloaded through GIT.  However, despite the 2208wfp being listed in the MonitorsDB, I still don't see it in the 'Screen and Graphics' section. (running dpkg-reconfigure can accurately 'name' it, but the driver used it still 'Plug n Play').  I tried filling in the Vertical and Horizontal values manually, and still no dice.  I just want 1680x1050 @ 60 hz.

At best I've got 1280x960 working, but in any attempt to go up to 1680x1050, I've had to pan the desktop to see its entirity.  The video card is an nVidia FX5200 pci with only one port (DVI).  Before I was using an adapter to connect it to the older analog-VGA-only monitor, but now I'm using an actual DVI cable, if it matters any.  Ubuntu version is 7.10 64-bit.

Any ideas before this alone sends me back to Windows?  (low res @ 22" is a severe eye-sore)

-Ray

---

### Post by pemdasi on 2008-04-11
I had this problem this morning.  Although I don't know if it will still be any help to you, this is what I did to fix the problem.

This is my xorg.conf, I have an ati graphics card:

```

Section "Files"
EndSection

Section "Module"
	Load		"GLcore"
	Load		"glx"
	Load		"dbe"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection


Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"ati2600"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Dell_2208wfp"
	Vendorname	"Dell"
	Modelname	"Dell 2208WFP(Analog)"
	Horizsync	31.0-83.0
	Vertrefresh	56.0-75.0
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ati2600"
	Monitor		"Dell_2208wfp"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes	"1680x1050" "1440x900"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "ServerFlags"
EndSection



```

---

### Post by SupraBlur on 2008-04-11
Oddly I switched my cable to VGA instead of DVI and everything detected ok.  The point is moot since I've since switched to Mac OSX.  Snags like this and others made me just want the simplicity and support of a commercial OS, even if it meant paying for it.

-Ray

---

