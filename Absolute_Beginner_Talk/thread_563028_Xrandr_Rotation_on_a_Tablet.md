---
title: "Xrandr Rotation on a Tablet"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by High Camp on 2007-09-29
Hello helpful people,

Thanks for taking the time to read and possibly answer my post. I've been searching for weeks (it's not high priority) to find a solution for rotating my tablet screen. I think the reason none of the solutions are working for me is because I'm running Xubuntu. 

I found this post: [http://ubuntuforums.org/showthread.php?t=301380&highlight=xrandr+error+12&page=2](http://ubuntuforums.org/showthread.php?t=301380&highlight=xrandr+error+12&page=2)
I think it answers my questions and solves my problem but I can't use it yet. It sounds like in Ubuntu there is a simple option to allow screen rotation:
> Also make sure you can set your screen rotation via the System > Preferences > Screen Resolution.
In Xubuntu I don't have this option so I assume that means I need to edit my xorg.conf file by adding "RandRRotation" "On". I know were my xorg.conf file is, I know how to edit it. What I don't know is were in the file to edit and what exactly I should put in?

Also, while looking around in xorg.conf I came across a section on screen resolution. I used to use my screen at 1280x1024. Is it possible to edit this section to include that resolution?

Thanks much,

---

### Post by olejorgen on 2007-09-29
```
/usr/bin/xrandr --orientation inverted
```
What happens if you run this script?

---

### Post by High Camp on 2007-09-29
I get this error:
> simon@simon:~$ /usr/bin/xrandr --orientation inverted
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  156 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12

Thanks,

---

### Post by High Camp on 2007-09-29
olejorgen, thanks for your reply.

Does anyone have any thoughts on this. I'm pretty sure I just need to edit the xorg.conf file but don't want to mess with it because from what I understand that could serious mess with my display settings.

Thanks,

---

### Post by olejorgen on 2007-09-29
You have added the randr option, right? Maybe you should post you xorg.conf?

---

### Post by High Camp on 2007-09-29
> **olejorgen said:**
> You have added the randr option, right? Maybe you should post you xorg.conf?

Ma ha ha. Sorry I have to laugh. I have not added the randr option to the xorg.conf file because I am trying to figure out exactly what to add and were.

Here it is: (I wrapped it in code tags so it would scroll)
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
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"nVidia Corporation NV43 [GeForce Go 6200/6400]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV43 [GeForce Go 6200/6400]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

Thanks again for your help, I really appreciate it.

P.S. At the same time if you can suggest adding 1280x1024 screen resolution in there it would be even more appreciated (not that I can appreciate this any more than I already do).

---

### Post by High Camp on 2007-09-29
Wait a minuet. I think I see it now. Would this be correct?
> Section "Device"
	Identifier	"nVidia Corporation NV43 [GeForce Go 6200/6400]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	**Option		"randr"	           "on"**
EndSection

---

### Post by olejorgen on 2007-09-29
ups.. sorry about that :P must learn to readposts properly.

```

Option "RandRRotation"  "true"

```
should be added under the display section.
ie.
```

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV43 [GeForce Go 6200/6400]"
	Monitor		"Generic Monitor"
	**Option "RandRRotation"  "true"**
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"
	EndSubSection

```

---

### Post by olejorgen on 2007-09-29
To add 1280x1024 as a mode just add a new
```

SubSection "Display"
		Depth	24
		Modes		"1028x1024"
	EndSubSection

```
This will most likely work.

As alwas take a backup of xorg.conf and be sure you know how to restore* it in case something goes wrong. 

* sudo mv <path to copy> /etc/X11/xorg.conf

---

### Post by High Camp on 2007-09-30
Hey

Sorry I haven't gotten back to you sooner. I learned a valuable lesson last night. That lesson being that changing the resolution in xorg.conf will severely F*** your system. I made the two changes and then rebooted and the system was unable to load the xserver. I still had the text based interface so I went in and removed the two changes I had made to the file but that still didn't do anything. I then removed the xserver with aptitude and went to reinstall it but my network card wasn't loading properly either so I couldn't connect to the repositories. Long story short, I reinstalled Xubuntu last night. 

The lesson here for anyone else reading this: DO NOT CHANGE THE SCREEN RESOLUTION unless you know what you're doing.

This morning I gingerly tried adding the RandRotation option. It did not screw with my computer but it also did not work. I'm currently looking around on the internet for some other resources I've found. I'll post as soon as I have more info.

Thanks, if anyone else has any thoughts please share.

Note: I'm blown away at how fast and easy it was to reinstall Linux. When I was using M$ I would format and reinstall ever 3-6 months and that was a day long procedure. In this case it took me 20 min. to install and 30 min. to get all the programs I had before.

---

### Post by olejorgen on 2007-09-30
Hm.. if you undid them properly, it should've worked. But it's always better to restore an copy. That way you're sure that the file should work.

You can also do ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` to restore your xorg.conf to "factory settings".

---

