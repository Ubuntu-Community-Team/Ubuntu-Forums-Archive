---
title: "Wacom Tablet GD model"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by alexgouk on 2007-04-28
Trying to configure my USB  Wacom, the cursor moves but not over the whole screen nor does it appear to be pressure sensitive. 
The Gimp says there are no extended input devices
I have Wacom Tools downloaded but I dont know how to use or even find them.

My  /etc/X11/xorg  file reads as follows

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/wacom"# Change to 
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
	# /dev/input/event
	# for USB
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/wacom"# Change to 
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
	# /dev/input/event
	# for USB
EndSection

Can some kind person point me in the right direction?
Thanks

---

### Post by burt_57 on 2007-05-25
Look over at that link
[http://linuxwacom.sourceforge.net/index.php/howto/main](http://linuxwacom.sourceforge.net/index.php/howto/main)

---

