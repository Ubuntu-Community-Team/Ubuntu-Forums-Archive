---
title: "Editing Difficulties"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by rs148004 on 2007-11-15
Hello all,

I'm completely new to Ubuntu having only used it for the last two weeks, and not personally knowing anyone who runs it have left me with no one to turn to for support except you fine people.  I tried searching the forums for the solution to my current problem, but I think I'm just extremely unique.  The problem I've got is that whenever I try to edit a folder or file's name Ubuntu will not allow me to type anything.  This problem also presents itself with an inability to type in IMs over Pidgen and once or twice in the Open Office Word Processor, except within these applications all it takes is closing the app and restarting, or at worst a whole computer restart.  If anyone knows either what I'm doing wrong or whats going wrong with my folder editing it would save me from having fifty "untitled folders."

Thanks everyone!

---

### Post by Znort_Ubern00b on 2007-11-15
When you have finished renaming the folders do you press enter???

I found that if i don't it reverts back to original name.

---

### Post by TeaSwigger on 2007-11-15
Problem with the keyboard perhaps? Is this pretty consistent, in that when you have this problem, does it behave similarly in anything you'd use the keyboard in? If this sounds possible, is this keyboard and PC combination working fine in anything else, say windows, or is it only acting up in ubuntu? Of course rule out the cord from the keyboard not being seated right in the PC's socket. It's a pretty flimsy connection on one of my PCs. That ruled out, if it's only in ubuntu and sounds like a keyboard issue, please post the make and model of the keyboard (unless it's very generic) and what is in this file: /etc/X11/xorg.conf 

Hope you're enjoying yourself in ubuntu otherwise :)

---

### Post by rs148004 on 2007-11-15
I'm currently using a laptop (Dell Inspiron 6000), so the keyboard being plugged in is a non-issue.  I'm really thinking this is a software problem somewhere in the system because I can't even begin to type while trying to edit file and folder names in the file browser, and I've never had any keyboard problems in Windows XP.

As for the contents of my xorg.conf file here they are (I would edit out the useless stuff if I knew what you were looking for):

# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1920x1200"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by MyR on 2007-11-18
your configuration looks fine to me.
you could perhaps try disabling your desktop effects. i had a remotely similar problem one time dealing with switching between window managers
good luck!

peace

---

