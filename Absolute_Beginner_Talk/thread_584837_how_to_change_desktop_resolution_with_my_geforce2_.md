---
title: "how to change desktop resolution with my geforce2 mx/100 vga"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by maani_ch on 2007-10-21
i  tried to change my resolution from 640x480 to something higher but cant able to do it how to fix it

ection "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nv"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"FTD-G722AS2"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Monitor		"FTD-G722AS2"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection

please check what is wrong here thanks

---

### Post by mikeyphi on 2007-10-21
Assuming you are using Gutsy - What happens if you try to change resolution under System/Administration/ Screens & Graphics? And then also go to System/Preferences/Screen resolution to make the same setting?

---

### Post by Wibbe82 on 2007-10-30
> **mikeyphi said:**
> Assuming you are using Gutsy - What happens if you try to change resolution under System/Administration/ Screens & Graphics? And then also go to System/Preferences/Screen resolution to make the same setting?

I have the exact same problem and I can't change the resolution through System/Preferences/Screen resolution.

System/Administration/ Screens & Graphics, I don't have this option in my menu. I'm using Ubuntu 7.04 if that makes any difference.

I'm completely new to this (Ubuntu) so very basic instructions is preferable.

---

