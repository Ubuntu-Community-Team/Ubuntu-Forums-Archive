---
title: "All qt4 demo/examples fail because monitor reports 0mm x 0mm?"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by Blatpho on 2008-01-15
Not sure how to fix this, but I recently tried to run the qt4 demos & examples, and they all come back with Floating point exception (crash dump).

I got some info on IRC that it is because when I do  xrandr I get :
```
default connected 1152x864+0+0 0mm x 0mm
   1280x1024      60.0     47.0     43.0  
   1152x864       75.0*    70.0     60.0     47.0     43.0  
   1024x768       85.0     75.0     72.0     70.0     60.0  
   800x600        85.0     75.0     72.0     70.0     60.0     56.0    100.0     90.0  
   640x480        85.0     75.0     72.0     60.0    120.0    100.0     90.0  
   720x576        60.0  
   640x400        75.0     60.0  
   400x300        75.0     60.0  
   320x240        75.0     60.0  
   320x200        75.0     60.0  
```

The issue is the 0mm x 0mm.  Qt takes those values, and well, gets a crash.

The monitor is a IIYAMA 8617E, the gfx card is a ATI Radeon 9600.
The xorg.conf file has:
```
Section "Files"
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
	Identifier	"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Driver		"fglrx"
	Busid		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection
```


I already tried to set my monitor to the correct model, but on reboot, I don't get a screen, and it says starting in safe mode, and gives me the option of picking monitor again.  Well, this can go on forever.  I need to keep the generic model for some reason.

Anyway, any ideas how I can fix this issue so I can run qt demos/examples/aps ?

TIA!

---

