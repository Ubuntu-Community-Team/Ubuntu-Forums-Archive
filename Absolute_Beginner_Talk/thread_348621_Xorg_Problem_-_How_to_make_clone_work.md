---
title: "Xorg Problem - How to make clone work?"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by MrJackdaw on 2007-01-29
I specifilcally want my laptops output to be cloned whenever an external input is in place. Currently I have the external outputs working :) but not cloned :( Trying TV-out first. I have tried Option "Clone" "true" in many places, but none of them seem to work. Ideas?

Here is my current Xorg - honed after many faliures, it still bears some of the scars! I have trimmed it to where the monitor stuff starts...

```
 #Beginning of monitor preferences...

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Device"
	Identifier "LCD_CRT"
	Driver "i810"
	Option "MonitorLayout" "CRT,LFP"
	Screen 0
	BusId "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "CRT"
	Driver "i810"
	Option "MonitorLayout" "CRT,LFP"
	Screen 1
	BusId "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "LCD_TV"
	Driver "i810"
	Option "MonitorLayout" "TV,LFP"
#    	Option "Clone" "true" # Do I put this here or in the TV device?
	Screen 0
	BusId "PCI:0:2:0"
	Option     "IgnoreEDID" "true" #Here?
EndSection

Section "Device"
	Identifier "TV"
	Driver "i810"
	Option "MonitorLayout" "TV,LFP"
	Option "TVStandard" "PAL-M"
	Option "TVOutFormat" "SVIDEO" # "Composite" or "SVIDEO" or "RBG"
	Option "ConnectedMonitor" "TV" 
	Screen 1
	BusId "PCI:0:2:0"
#	Option "Clone" "true" #Lets see if it works here :)
	Option     "IgnoreEDID" "true" #Here?
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Monitor"
	Identifier	"CRT"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Monitor"
	Identifier "TV"
	HorizSync	30-50
	VertRefresh 60
EndSection


Section "Screen"
	Identifier	"LCD_CRT"
	Device		"LCD_CRT"
	Monitor		"LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"LCD_TV"
	Device		"LCD_TV"
	Monitor		"LCD"
EndSection

Section "Screen"
	Identifier "CRT"
	Device "CRT"
	Monitor "CRT"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "TV"
	Device "TV"
	Monitor "TV"
	DefaultDepth 24
	Subsection "Display"
		Depth 24
		Modes "1024x768" "800x600"
	EndSubsection
EndSection

Section "ServerLayout"
	Identifier "LCDandTV"
	Screen 0 "LCD_TV"
	Screen 1 "TV"  RightOf "LCD_TV"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerLayout"
	Identifier "LCDandCRT"
	Screen 0 "LCD_CRT"
	Screen 1 "CRT" RightOf "LCD_CRT"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerLayout"
	Identifier "LCDOnly"
	Screen 0 "LCD_CRT"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerFlags"
#	Added Xinerama support to see if it helps the crashing issue 2/1/07
#	Xinerama stops Crossover crashing, but there are window wrapping issues...
# 	Option "xinerama" "true"
	Option "DefaultServerLayout" "LCDandTV"
#	Option "DefaultServerLayout" "LCDandCRT"
#       Option "DefaultServerLayout" "LCDOnly"
EndSection

Section "DRI"
	Mode	0666
EndSection
 
```

My computer is a Dell Inspiron 6000 and boots only Ubuntu now. 

James

---

