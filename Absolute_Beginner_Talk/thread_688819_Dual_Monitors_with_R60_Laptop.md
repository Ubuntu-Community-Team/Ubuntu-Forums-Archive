---
title: "Dual Monitors with R60 Laptop"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by Cloey64 on 2008-02-05
I am dual booting Ubuntu 7.10 and XP on my R60 Laptop at the moment. I will have a nice 22" monitor on the way soon and I would like to be able use both monitors when I am in my room (different screens on each monitor [either different workspaces or one workspace spread between the two] ) but then relatively easily switch to just my laptop screen when I leave the room and go to class. I will be shutting down my laptop before switching between display settings so that sound alleviate some of the problems.

This is the section of my xorg file that refers to my display
> 
Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Driver		"intel"
	option		"VBERestore"		"false"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768" "720x400" "640x480"
	EndSubSection
EndSection


I know to use a Live CD to get the information on my monitor to put into the Xorg file but where do I go from there. Should I use the GUI in System for displays? Is there a program to use? Any help would be appreciated.

---

### Post by talsemgeest on 2008-02-06
You should be able to simply add another screen in "screens and graphics"

Hope I've helped :)

---

