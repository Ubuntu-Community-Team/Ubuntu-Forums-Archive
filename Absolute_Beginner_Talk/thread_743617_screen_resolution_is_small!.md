---
title: "screen resolution is small!"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by drmoore1 on 2008-04-02
My screen is tiny. It only allows me to use 800x600. Since I am using virtualbox, I have heard that ubuntu not using the virtualbox driver for the screen could do this, but I am not sure how to fix it as this person was using it on a another linux host. Anyway here is my etc/x11/xorg.conf file:

```
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
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"800x600"
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
```

How can I fix this?

---

### Post by xXeneXx on 2008-04-02
> **drmoore1 said:**
>  Since I am using virtualbox...

I was in the same boat, then some nice people (Here on the forums) told me to get the entire Ubuntu experience. C'mon, do the same. :)

---

### Post by drmoore1 on 2008-04-04
anybody? There has to be some way to fix this.

---

### Post by Therion on 2008-04-04
Have you tried using the following command in a Terminal?
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by drmoore1 on 2008-04-04
yep and I get a no bootable medium found error. I'm not too sure what to select when running that anyway though so I don't know if that is why it messes up.

---

### Post by bubba_169 on 2008-04-04
On the line modes "800x600" under section SCREENS, could you add more options? Im sure I've had to do this before and I think you would use it like:

```
Modes "800x600" "1024x768" "1152x864" ...
```

---

### Post by kerry_s on 2008-04-04
change->
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"800x600"
	EndSubSection
EndSection
```

to

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection
```

then restart X (ctrl+alt+backspace, at the log in screen)

---

### Post by Therion on 2008-04-04
So when you run the command it's allowing you to adjust your settings then?  Okay that's good.  The gist of what you want to do is this.  Just accept the default settings for everything (use your Tab key to move through the menus) until you get to the section that deals with monitor resolution.

Going by memory here, but I think you'll see a window with some common monitor resolutions in it.  Selected resolutions will be really low ones (480x600, 600x800 etc.) and have something that looks like:  [*] to indicate they have been "selected".  These are your available resolutions, and most likely they all suck.  We're going to change that...

The trick here is, the window only shows you **some** of the available resolutions.  You can scroll up to get to more reasonable resolutions (1024x768, 1440 x900 and so forth).  Now the thing is, the HIGHEST resolution you choose here will be the new DEFAULT resolution.  So, remove the "*" from the crappy resolutions (use the space bar to remove it), and turn on three "good" resolutions by putting an "*" in the higher resolutions... Remembering that the highest one you choose will be used by default after you save and reboot your PC.

---

### Post by drmoore1 on 2008-04-04
Still no luck, I wind up with a no bootable medium found. Using both of these methods.

---

### Post by Therion on 2008-04-04
> **drmoore1 said:**
> Still no luck, I wind up with a no bootable medium found. Using both of these methods.
Okay, that's not making sense to me...  

Are you running Ubuntu from a LiveCD or an install to your hard drive?

---

### Post by s3a on 2008-04-04
"sudo dpkg-reconfigure -phigh xserver-xorg" then choose your resolution

P.S.
Do not enter the quotation marks "" in the terminal windows. I assume you know how to open a terminal window..

---

### Post by drmoore1 on 2008-04-04
I'm running it through virtualbox, a virtual pc.

---

### Post by Therion on 2008-04-04
> **drmoore1 said:**
> I'm running it through virtualbox, a virtual pc.
That's your problem right there.  

If you just want to experiment with Ubuntu you're better off using a LiveCD in my opinion.

**@ s3a:**  You're a little late to the party...  See previous posts.

---

### Post by drmoore1 on 2008-04-04
I can't use any applications with live cd though because I can't save to the cd right? And also, this same configuration works fine on my other computer.

---

### Post by Therion on 2008-04-04
> **drmoore1 said:**
> I can't use any applications with live cd though because I can't save to the cd right? And also, this same configuration works fine on my other computer.
Not sure what to tell you... Maybe try installing using [Wubi](http://wubi-installer.org/).

---

### Post by drmoore1 on 2008-04-06
I am now using wubi and it is awesome. Thanks.

---

