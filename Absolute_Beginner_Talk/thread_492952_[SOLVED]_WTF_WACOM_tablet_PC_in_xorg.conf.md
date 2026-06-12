---
title: "[SOLVED] WTF: WACOM tablet PC in xorg.conf???"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Beatbreaker on 2007-07-05
hey, i've just noticed this in my xorg.conf

there's 3 entries for a WACOM tablet PC as in input device in my xorg.conf. The funny thing is that i don't own a tablet PC of any description at all for my computer - can i delete these entries? (after backing up my xorg.conf of course)

i also noticed it in this guys xorg.conf - [http://ubuntuforums.org/showthread.php?t=492249](http://ubuntuforums.org/showthread.php?t=492249) - this stuff shouldn't be on our systems right?? (unless we of course do actually own 3 wacom tablets for the one PC)


```
Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
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
    Identifier "Configured Mouse"
    Driver "mouse"
    Option "CorePointer"
    Option "Device" "/dev/input/mice"
    Option "Protocol" "ExplorerPS/2"
    Option "Buttons" "7"
    Option "ButtonMapping" "1 2 3 6 7"
    Option "Emulate3Buttons" "false"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"A201P1"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV43 [GeForce 6600 GT]"
	Monitor		"A201P1"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1400x1050"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1400x1050"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1400x1050"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1400x1050"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1400x1050"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1400x1050"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
```

---

### Post by ZenobiaBE on 2007-07-05
I have four pc's with the same configuration by default, none have a wacom tablet. I just deleted these sections and didn't notice any problems or changes.

---

### Post by Seisen on 2007-07-05
I think everybody has that in their xorg.conf file by default, if you don't have a wacom tablet then you can erase them.

---

### Post by southernman on 2007-07-05
It isn't something to get all bent over! ;)

Yes, you can delete them. Be sure to remove the 3 entries at the bottom of the file for wacom also, or you'll have a glitch.

---

### Post by Beatbreaker on 2007-07-05
> **southernman said:**
> It isn't something to get all bent over! ;)

Yes, you can delete them. Be sure to remove the 3 entries at the bottom of the file for wacom also, or you'll have a glitch.

haha yeah it's everyones fault this has happened!! j/k - i was mainly worried that i did something stupid that could potentially screw with my system.

thankx everyone for the tips, i'll go ahead and do that -

---

### Post by Beatbreaker on 2007-07-06
just a note, i gave it a go lasntight and it worked like a charm - i think that my boot time has even increased between the log in screen and my desktop now too

(or it may just be a placebo ettect, not sure :o ) 

eitherway thanks for the help once again!

---

