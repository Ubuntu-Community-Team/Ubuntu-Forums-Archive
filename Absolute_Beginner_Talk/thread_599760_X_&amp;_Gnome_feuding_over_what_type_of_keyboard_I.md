---
title: "X &amp; Gnome feuding over what type of keyboard I have"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by cathuria on 2007-11-01
Hi, folks!
Every time I log in, I get this error message "The X system keyboard settings differ from your current GNOME keyboard settings."; one expects a pc101 and the other expects a pc105.
I actually use an MS Digital Media Pro, if anyone knows a profile similar to that (it isn't in the keyboard applet list).  This started happening, I believe, after I uninstalled the proprietary drivers for my ATI card (that didn't go well).  Perhaps something in that operation confused the whole keyboard thing.
Anyhow, how do I tell both X and Gnome that I have just one keyboard?
Thanks.

---

### Post by llamakc on 2007-11-01
Hit the keys: ctrl-alt-F2 to get to the 2nd tty console. Login as your user.

Type the following:

```

sudo dpkg-reconfigure xserver-xorg

```

And keep the defaults but when you get to the keyboard section, make the choice that you want (or corresponds to whatever is correct).

Restart GDM

```

sudo /etc/init.d/gdm restart

```

Login and make sure your settings in the GNOME menu System | Preferences | Keyboard are what yo want.

---

### Post by cathuria on 2007-11-01
Thanks -- but hey, you might want to mention that a fella should print out or memorize the instructions first, because they won't be able to see them once they hit ctrl-alt-f2:eek:

Anyhow, I went through all that, and now both xorg.conf and the keyboard preferences in gnome say that I have the same generic 104 keyboard.  BUT... Gnome still complains that it expects a 101 board every time I log on.  Which is quite weird since everything I can see says I have a 104...

Linux gremlins...:)

---

### Post by llamakc on 2007-11-01
Please post your /etc/X11/xorg.conf

Thanks.

---

### Post by cathuria on 2007-11-01
Here 'tis:

```

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
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
	Identifier	"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"DELL 2405FPW"
	Option		"DPMS"
	HorizSync	30-75
	VertRefresh	30-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Monitor		"DELL 2405FPW"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

---

### Post by cornelius2 on 2007-11-04
I had the exact same problem at every login with pc104 selected in both xorg.conf and gnome keyboard layout settings. I searched for pc101 (that the dialog was complaining about) in gconf-editor (Applications / System Tools / Configuration Editor) and found it in this key:

/desktop/gnome/peripherals/keyboard/kbd.sysbackup/model

Changing the pc101 value there to pc104 solved the problem for me.

BTW this problem usually reappears when I install or remove Xgl.

---

