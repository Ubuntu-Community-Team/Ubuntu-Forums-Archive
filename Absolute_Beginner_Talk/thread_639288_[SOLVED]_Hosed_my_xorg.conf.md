---
title: "[SOLVED] Hosed my xorg.conf?"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by OttoDestruct on 2007-12-13
I have no idea what I just did to my xorg.conf (unfortunately I didn't make a backup either). I was just messing with some mouse settings, restarted X, and it starts flipping out about having to run in a low graphics mode, and something about my keyboard settings. Whats going on? Is there a way to just generate a new one since I have no idea what broke?

Heres my xorg.conf

> Section "Files"
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
	Identifier	"Generic Video Card"
	Driver		"ati"
	BusID		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"L90D+ DVI"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"L90D+ DVI"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
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
EndSection

---

### Post by LaRoza on 2007-12-13
Well, the first thing one would do, is restore from the backup before editing system files. In leiu of that, I would undo whatever you did.

(Someone posted the command before I remembered the exact syntax.)

---

### Post by Rocket2DMn on 2007-12-13
Yeah, the command is
```
sudo dpkg-reconfigure xserver-xorg
```
That takes you through the xorg setup - everything from mouse and keyboard to video drivers and monitor resolutions.
Then restart X with CTRL+ALT+BACKSPACE

---

### Post by OttoDestruct on 2007-12-13
> **LaRoza said:**
> Well, the fist thing one would do, is restore from the backup before editing system files. In leiu of that, I would undo whatever you did.

I didn't make a backup.

I have no idea what I changed to screw things up - all I was doing was messing with mouse stuff.

---

### Post by PmDematagoda on 2007-12-13
If you want an xorg.conf file with the default settings then kill the GUI using:-

```
sudo /etc/init.d/gdm stop
```

And configure the X-server to the defaults using:-
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

After that is done do:-

```
sudo /etc/init.d/gdm start
```

To bring back the GUI which should be fixed.

---

### Post by LaRoza on 2007-12-13
> **OttoDestruct said:**
> 
I have no idea what I changed to screw things up - all I was doing was messing with mouse stuff.

Do the above command, and consider being more careful next time when editing system files with "sudo"

---

### Post by Rocket2DMn on 2007-12-13
> **LaRoza said:**
> Do the above command, and consider being more careful next time when editing system files with "sudo"

Better yet, have a blast trying out some new stuff, just make a backup first!

---

### Post by OttoDestruct on 2007-12-13
> **Rocket2DMn said:**
> Better yet, have a blast trying out some new stuff, just make a backup first!

This is what I was trying to do :(

---

### Post by OttoDestruct on 2007-12-13
The xserver.org reconfigure stuff worked - except gnome is still complaining now that my xorg conf has 105 keys and it still has something like 101 :confused:

[IMG]http://i13.tinypic.com/7xmuzbq.jpg[/IMG]

---

### Post by Rocket2DMn on 2007-12-13
If what you had worked before, might as well stay with 101 (GNOME), but 105 (X) will probably work, too.

---

### Post by mdpalow on 2007-12-13
You should have a back-up already even if you didn't know it. Look in your /etc/X11 folder and look for xorg.con~. You might have to press CTRL+H to view hidden files.

---

### Post by OttoDestruct on 2007-12-13
> **Rocket2DMn said:**
> If what you had worked before, might as well stay with 101 (GNOME), but 105 (X) will probably work, too.

Problem is I'm getting this message every time I restart X apparently. How do I get it to quit asking? It works no matter what I choose.

---

### Post by Rocket2DMn on 2007-12-13
> **OttoDestruct said:**
> Problem is I'm getting this message every time I restart X apparently. How do I get it to quit asking? It works no matter what I choose.

Hehe, make a backup of your xorg.conf file:
```
sudo cp /etc/X11/xorg.conf /etx/X11/xorg.conf.backup
```
Then open the file and under the keyboard section replace "pc105" with "pc101"
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by OttoDestruct on 2007-12-13
That fixed it, thanks.

Back to the way it was.

---

### Post by meindian523 on 2007-12-13
well,if it's done,please mark the thread as solved....

---

### Post by azizzle on 2007-12-15
how do i restore my backed up xorg?

---

### Post by meindian523 on 2007-12-17
just remove the ".backup" part so that the file is now named xorg.conf and remove the xorg.conf you want to replace.

---

