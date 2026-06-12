---
title: "Lend me your iBook 800 xorg.conf !"
date: 2005-05-02
forum: Apple PPC Users
---

### Post by joebolte on 2005-05-02
Hi all,
I have a doozy of a problem with getting my graphics card autodetected.  I have posted in a couple different places, but nothing I try has any effect.  Could someone with an 800Mhz iBook G3 please post their /etc/X11/xorg.conf file so that I can try one that is already working on the same model? I would appreciate it so much.

Thanks,
Joe

---

### Post by mikji on 2005-05-04
I have a 700Mhz iBook G3, this is what I use. Far as I know, it should work.

---------------------------------

# xorg.conf (x-org X Window System server configuration file)

Section "Files"
	FontPath	"unix/:7100"
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/Speedo"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "ServerFlags"
        Option          "BlankTime"             "0"
	Option          "StandbyTime"           "0"
	Option          "SuspendTime"           "0"
	Option          "OffTime"               "10"
EndSection

Section "Module"
	Load		"GLcore"
	Load		"bitmap"
	Load		"dbe"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"record"
	Load		"speedo"
	Load		"type1"
	Load		"v4l"
	Load		"vbe"
	Load		"xtt"
EndSection

Section "Extensions"
#	Option		"Composite"		"Enable" 
        Option		"RENDER"		"true"
        Option		"DAMAGE"		"true"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"		"xfree86"
	Option		"XkbModel"		"pc105"
	Option		"XkbLayout"		"dvorak"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9000 M6 (R250 LY)"
	Driver		"radeon"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"true"
	Option 		"AGPMode" 		"4"
	Option          "AGPSize" 		"16"
	Option		"RenderAccel"		"true"
	Option		"AllowGLXWithComposite"	"true"
        Option          "backingstore"          "true"
EndSection

Section "Monitor"
	Identifier	"Color LCD"
	HorizSync	28-49
	VertRefresh	43-72
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 9000 M6 (R250 LY)"
	Monitor		"Color LCD"
	DefaultDepth	16
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
	SubSection "Display"
		Depth		8
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
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

