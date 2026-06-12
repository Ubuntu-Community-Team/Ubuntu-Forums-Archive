---
title: "TV out again"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Sin@Sin-Sacrifice on 2007-10-20
Alright.... I've spent the better part of the last 3 months trying to find something on this. Anything at all. I have an NVIDIA GeForce 6150 chipset, AMD blah blah blah and a will to watch my movies on my TV. I have a cheap Insignia TV from best buy but it has 3 Composite ins, 1 out, 1 SVIDEO in, and another one. My PC has 2 composite RCA jacks and 2 SVIDEO jacks. Anyway.... I've been trying to get tv out in both ubuntu and vista for a while now. In ubuntu I found, after upgrading to gutsy, everything it would seem I need is in the xorg.conf file already. It looks like this

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
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

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Device[0]"
	Driver		"nvidia"
	Busid		"PCI:0:13:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	screen 0
EndSection

Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device[1]" 
   	Screen 1 
   	Option          "TVOutFormat" "Composite" #or SVIDEO etc 
   	Option          "TVStandard" "NTSC" #or NTSC etc 
   	Option          "ConnectedMonitor" "Monitor[1]" 
   	BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection

Section "Monitor"
	Identifier	"Monitor[0]" #CRT
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Monitor" 
    Identifier "Monitor[1]" #TV 
    HorizSync 30-50
    VertRefresh 50 
 EndSection

Section "Screen"
	Identifier	"Screen[0]"
	Device		"Device[0]"
	Monitor		"Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "Screen" 
   	Device "Device[1]" 
   	Identifier "Screen[1]" 
   	Monitor "Monitor[1]" 
   	DefaultDepth 24 
       	SubSection "Display" 
               Depth 24 
               Modes "544x372_50" 
       	EndSubSection    
EndSection

Section "ServerLayout"
	Identifier	"Simple Layout"
  screen 0 "Screen[0]"
  screen 1 "Screen[1]" RightOf "Screen[0]"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Why doesn't it work?? I've switched the refresh rate to 50 from 60 and changed the TV Standard from Pal-G to NTSC-G and just NTSC, gone over it over and over again comparing it to what I've found online and nothing there seems off. Yet every time I restart X.... I just get the AV1 in the corner.... I got the same results in Feisty when I added everything myself about 3 weeks ago. Anyone out there know what's going on?

---

