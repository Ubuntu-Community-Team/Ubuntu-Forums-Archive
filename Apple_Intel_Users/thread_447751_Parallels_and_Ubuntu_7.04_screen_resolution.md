---
title: "Parallels and Ubuntu 7.04 screen resolution"
date: 2007-05-18
forum: Apple Intel Users
---

### Post by kaveh1000 on 2007-05-18
I cannot get a higher resolution than 1024 x 768. I have tried several methods on these forums and elsewhere, but no joy. Can someone suggest a procedure that works?

---

### Post by jdemesse on 2007-05-18
Adjust /etc/X11/xorg.conf and add more resolutions in the Screen section.

For example:

[FONT="Courier New"]Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI RADEON X1900XT"
	Monitor		"Apple Cinema Display 23"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1920x1200"	"1680x1050"	"1600x1200"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection[/FONT]

---

### Post by kaveh1000 on 2007-05-18
Thank you. I tried that, and here is the portion of the file now:

.....
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x852" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x852" "1024x768" "800x600" "640x480"
......

This resolution is also set in the video part of the virtual machine.

I restarted Ubuntu and still get 1024, and in system > Screen resolution that is the highest available.

---

### Post by kaveh1000 on 2007-05-18
oh, I have added this resolution to all subsequent cases as well, with other depth displays.

---

### Post by Enverex on 2007-05-18
If you have a decent graphics card and monitor then the easier thing to do is delete all the screenmodes from the config and it will detect what it can do automatically when X starts.

---

### Post by kaveh1000 on 2007-05-18
OK. I deleted the following section:

Section "Screen"
...
EndSection

But it complained and remained in command line mode. Somehow I recovered the original file and back where I was. 

I am a newbie to Linux, remember. ;-)

---

### Post by Enverex on 2007-05-18
lol, you don't remove all that, just these...

SubSection "Display"
Depth 1
Modes "1440x852" "1024x768" "800x600" "640x480"
EndSubSection

and again for each different "depth".

.e.g. here is mine.

```
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
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

Section "Device"
	Identifier	"nVidia Corporation G71 [GeForce 7900 GT/GTO]"
	Driver		"nvidia"
EndSection

Section "Monitor"
	Identifier	"VP930 Series"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G71 [GeForce 7900 GT/GTO]"
	Monitor		"VP930 Series"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by kaveh1000 on 2007-05-18
:-)

OK, thanks Enverex. I am running a MacBook Pro. But sometimes I am attaching that to an Apple 30" display. Do I need to give it the information about both monitors? 

At the moment I have "Generic monitor" and "Generic video card". I am a bit worried messing about with these, and not putting the correct info in.

---

### Post by kaveh1000 on 2007-05-19
OK guys, success, using this page:

[http://www.simplehelp.net/2007/04/30/how-to-increase-the-screen-resolutions-available-to-ubuntu-while-running-in-parallels-for-os-x/](http://www.simplehelp.net/2007/04/30/how-to-increase-the-screen-resolutions-available-to-ubuntu-while-running-in-parallels-for-os-x/)

I had done this before, but I had chosen a non-standard resolution, and it didn't work. Now I chose 1280X1024 and it works great.

---

