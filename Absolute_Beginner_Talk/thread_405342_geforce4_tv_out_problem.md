---
title: "geforce4 tv out problem"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by cele on 2007-04-09
I have HP laptop with geforce4 440 and i found some tutorials and tried to make my tv out to work but still no picture on TV. 
What to do next???

I'm running Ubuntu 6.10 and this is my xorg.conf:

***************************************************************************
Section "Device"
	Identifier	"Device[0]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
	screen 0
EndSection

Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device[1]" 
   	Screen 1 
   	Option          "TVOutFormat" "SVIDEO" 
   	Option          "TVStandard" "PAL-G" #or NTSC etc 
   	Option          "ConnectedMonitor" "Monitor[1]" 
   	BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection

Section "Monitor"
	Identifier	"Monitor[0]" #LCD
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Monitor" 
    Identifier "Monitor[1]" #TV 
    HorizSync 30-50
    VertRefresh 50 
 EndSection

Section "Screen"
	Identifier		"Screen[0]"
	Device		"Device[0]"
	Monitor		"Monitor[0]"
	DefaultDepth	16
	!!! i cut out some code from here too
EndSection

Section "Screen" 
   	Device "Device[1]" 
   	Identifier "Screen[1]" 
   	Monitor "Monitor[1]" 
   	DefaultDepth 24 
       	SubSection "Display" 
               Depth 24 
               Modes "1024x768_60" 
       	EndSubSection    
EndSection

Section "ServerLayout" 
   Identifier  "Simple Layout" 
       Screen 0 "Screen[0]" 
       Screen 1 "Screen[1]" RightOf "Screen[0]" 
   InputDevice "Configured Mouse" "CorePointer" 
   InputDevice "Generic Keyboard" "CoreKeyboard" 
EndSection
***************************************************************************

Sorry about little long post!

---

### Post by Maestro23 on 2007-04-09
Have you taken a look at this: [https://help.ubuntu.com/community/NvidiaTVOut?highlight=%28tv%29%7C%28out%29](https://help.ubuntu.com/community/NvidiaTVOut?highlight=%28tv%29%7C%28out%29)
or this: [https://help.ubuntu.com/community/NvidiaTVOutNewbieEdition?highlight=%28tv%29%7C%28out%29](https://help.ubuntu.com/community/NvidiaTVOutNewbieEdition?highlight=%28tv%29%7C%28out%29)

Good luck.

---

### Post by cele on 2007-04-09
I did everything like it's written in the tutorial but still can't make it work.
Is there a way to check if svideo is working? this is my present conf. if anyone can figure out something wrong!?

Anyway that's HP Compaq NX9105 with geforce4 420 with 32MB

****************************************************
Section "Device"
	Identifier	"Device[0]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
	screen 0
EndSection

Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device[1]" 
   	Screen 1 
   	Option          "TVOutFormat" "SVIDEO" 
   	Option          "TVStandard" "PAL-B" #or NTSC etc 
   	Option          "ConnectedMonitor" "Monitor[1]" 
   	BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection

Section "Monitor"
	Identifier	"Monitor[0]" #LCD
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Monitor" 
    Identifier "Monitor[1]" #TV 
    HorizSync 30-50
    VertRefresh 60 
 EndSection

Section "Screen"
	Identifier		"Screen[0]"
	Device		"Device[0]"
	Monitor		"Monitor[0]"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "Screen" 
   	Device "Device[1]" 
   	Identifier "Screen[1]" 
   	Monitor "Monitor[1]" 
   	DefaultDepth 24 
       	SubSection "Display" 
               Depth 24 
               Modes "1024x768_60" 
       	EndSubSection    
EndSection

Section "ServerLayout" 
   Identifier  "Simple Layout" 
       Screen 0 "Screen[0]" 
       Screen 1 "Screen[1]" RightOf "Screen[0]" 
   InputDevice "Configured Mouse"
   InputDevice "Generic Keyboard"
EndSection

---

