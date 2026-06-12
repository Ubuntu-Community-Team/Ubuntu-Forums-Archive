---
title: "mac keyboard configuration"
date: 2007-02-16
forum: Apple PPC Users
---

### Post by min_max9000 on 2007-02-16
I went through the whole "sudo dpkg-reconfigure xserver-xorg" thing and thought I had done all I could to set up my mac keyboard but to no avail. Really all I care about is getting my alt and command keys reversed to what I am accustomed to.

Can anyone help?

---

### Post by pxwpxw on 2007-02-16
In ubuntu breezy and dapper there is (on Desktop menu bar) 
 
 System: preferences:keyboard:layout options - have you tried that.
 
 I cant find it in xubuntu desktop though.

Otherwise, here are 2 keybord extracts from xorg.conf:
as installed.

 1. from an ibook, (xubuntu 610), with no alt key on right.

 Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
 EndSection


 2. from powermac G5 (ubuntu 606) with current apple keyboard.


 Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
 EndSection

 No problems with them.

 Post your mac model, ubuntu version, and copy of xorg.conf if you need more help.

---

### Post by min_max9000 on 2007-02-16
Machine Name: Power Mac G4
Machine Model: PowerMac3,6
CPU Type: PowerPC G4 (3.3)
Number Of CPUs: 1
CPU Speed: 1.25 GHz
L2 Cache (per CPU): 256 KB
L3 Cache (per CPU): 1 MB
Memory: 2 GB
Bus Speed: 167 MHz
Boot ROM Version: 4.4.8f2
Serial Number: XxxxxxxxxPC1

and this is the graphics set up:

ATI Radeon 9000 Pro:

Chipset Model: ATY,RV250
Type: Display
Bus: AGP
Slot: SLOT-1
VRAM (Total): 64 MB
Vendor: ATI (0x1002)
Device ID: 0x4966
Revision ID: 0x0001
ROM Revision: 113-99702-131
Displays:
Apple Cinema Display:
Display Type: LCD
Resolution: 1680 x 1050
Depth: 32-bit Color
Core Image: Not Supported
Main Display: Yes
Mirror: Off
Online: Yes
Quartz Extreme: Supported
Rotation: Supported
Display:
Status: No display connected

---

