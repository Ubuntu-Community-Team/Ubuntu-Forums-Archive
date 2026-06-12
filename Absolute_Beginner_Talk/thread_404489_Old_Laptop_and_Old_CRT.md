---
title: "Old Laptop and Old CRT??"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by kpm on 2007-04-08
Hello,
I thought I would attempt this laptop crt dual monitor set up again...  I did some time ago but kept killing xorg.conf so gave up. This time, I seem to have managed to keep it alive, but not gotten dual screens to work other than cloning one and other.  On top of that, the CRT is stuck at a 60Hz vertical refresh rate (even though I set it to be 85).  Ultimately, it would be nice if I can get dual monitor set up to work, but if not, the next best thing is to have the CRT with a high refresh rate (1280x1024@85Hz) and the laptop screen simply blank.  So, I was hoping if I posted the edited xorg.conf file, someone may be able to steer me in the right direction:
[HTML]
Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility M3 AGP 2x 0"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility M3 AGP 2x 1"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier    "Thinkpad LCD"
    Option		"DPMS"
	HorizSync	28-70
	VertRefresh	43-60
EndSection

Section "Monitor"
    Identifier    	"KDS CRT"
    Option		"DPMS"
    HorizSync		30-95
    VertRefresh    	50-120
EndSection

Section "Screen"
    Identifier    "Thinkpad LCD Screen"
    Device        "ATI Technologies, Inc. Rage Mobility M3 AGP 2x 0"
    Monitor        "Thinkpad LCD"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier    "KDS CRT Screen"
    Device        "ATI Technologies, Inc. Rage Mobility M3 AGP 2x 1"
    Monitor        "KDS CRT"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "ServerFlags"
	Option "Xinerama" "true"
EndSection

Section "ServerLayout"
	Identifier	"Twin Head"
	Screen		"KDS CRT Screen"
	Screen		"Thinkpad LCD Screen" RightOf  "KDS CRT Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
[/HTML] 

Thanks

---

### Post by dstew on 2007-04-08
Is the "ati" driver really optimal for this card? I had a laptop with an ATI M4 card, and it would not work until I used the "vesa" driver. I have not, however, tried to use dual monitors with the laptop. I might try it this week though.

---

### Post by Straevaras on 2007-04-08
If anyone could shed some light on this, I'm trying to accomplish about the same thing, too.  I have a laptop hooked up to an HP vs17e LCD Monitor and I changed it like kpm has his above but it's still just copying the same image off my laptop display.  Although it looks like I did manage to get them to display in different resolutions (my laptop display is native 1400x1050 while the LCD monitor is native 1280x1024).

Here's my xorg.conf:

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"HP LCD"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh    	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"HP LCD Screen"
	Device		"ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Monitor		"HP LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "ServerFlags"
	Option "Xinerama" "true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	Screen 		"HP LCD Screen" RightOf "Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

But it would be awesome if I could get this to work.  Also on a side note, does anyone know how to bring Ubuntu down to runlevel 3?  Init 3 doesn't seem to work for me.

Thanks
-Strae

---

