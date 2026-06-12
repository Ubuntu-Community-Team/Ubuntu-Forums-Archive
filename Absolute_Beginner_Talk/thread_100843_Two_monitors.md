---
title: "Two monitors"
date: 2005-12-08
forum: Absolute Beginner Talk
---

### Post by nerdman on 2005-12-08
```
Section "Device"
	Identifier	"NVIDIA Corporation NV6 [Vanta/Vanta LT]"
	Driver		"nvidia"
	BusID		"PCI:1:7:0"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation GeForce 5200"
	Driver		"nvidia"
	BusID		"AGP:1:0:0"
EndSection

Section "Monitor"
	Identifier	"PionexMonitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Monitor"
        Identifier      "DellMonitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"VantaScreen"
	Device		"NVIDIA Corporation NV6 [Vanta/Vanta LT]"
	Monitor		"PionexMonitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "PionexMonitor"
	Screen		1 "DellMonitor" RightOf "PionexMonitor"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection
```

/etc/X11/xorg.conf

...what's wrong with it? If I plan on putting a third monitor, should I use the nVidia Twin View (Since both cards are nVidia) ?

---

