---
title: "Dual Monitors"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by mmikelst on 2007-04-20
This is probably a silly question....But how exactly do I get dual monitors running? I've got the 3-d NVIDIA drivers in place (I do have an NVIDIA card as well), but I'm not sure where to go from here...It's detecting my monitor plugged into my VGA port, but not the one plugged in through my DVI. Any help would be greatly appreciated!

---

### Post by mmikelst on 2007-04-20
bump...Anyone have any ideas?

---

### Post by amegli on 2007-04-20
Are the monitors the same resolution?

Do you want 2 separate desktops, or one giant one?

Your Nvidia card probably supports Twinview, which can span your desktop across both monitors and allow you to move windows back and forth, which may or may not be the behavior you desire.  Personally, that's what I use.  You can specify the appropriate Twinview options in your xorg.conf file ( /etc/X11/xorg.conf ).  You can also use the open source Xinerama.  This page gives some detail on the available options and how to use them - [http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)



-Andrew-

---

### Post by Alterax on 2007-04-20
The following is a snippet from my xorg.conf file.  I am running dual monitors using an ATI Radeon X1300, so you'll need to modify yours based on the structure of this one.  It should give you some ideas.  Will be on later in case you need help.


--Alterax



Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "dbe"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "v4l"
	Load  "vbe"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Radeon X1300"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Radeon X1300"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "800x600"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "800x600"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "800x600"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "800x600"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "800x600"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

---

### Post by mmikelst on 2007-04-20
Okay, these all helped a lot! I'm currently watching "A Scanner Darkly" on one monitor and typing this on the other!:) yay for dual monitors!

---

