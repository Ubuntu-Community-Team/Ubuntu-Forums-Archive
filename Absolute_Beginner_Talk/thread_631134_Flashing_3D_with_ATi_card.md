---
title: "Flashing 3D with ATi card"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by SilverAdder on 2007-12-04
Ive installed Gutsy on my laptop with a Mobility X1600. I installed the proprietary drivers thanks to envy and everything is working fine, until i start some 3D stuff. The are some weird flashing going on. Sometimes once or twice a second the screen flashes shortly Anything that can be done about that? 

Thanks in advance.

---

### Post by GSF1200S on 2007-12-04
> **SilverAdder said:**
> Ive installed Gutsy on my laptop with a Mobility X1600. I installed the proprietary drivers thanks to envy and everything is working fine, until i start some 3D stuff. The are some weird flashing going on. Sometimes once or twice a second the screen flashes shortly Anything that can be done about that? 

Thanks in advance.

While the following thread started and stayed primarily an nvidia thread, some ati guys showed up with the same problem. 

Im in there too, and I tried EVERYTHING, and I never did fix it. But, once installing 64bit, my problem (knock on wood), instantly went away. I dont know if the drivers are flawed for 32bit Ubuntu or what, but for some people the problem never went away. Try it though- some people solved there flashing problem and posted there methods. I thought I fixed mine at least 5-6 times..

[http://ubuntuforums.org/showthread.php?p=3873065#post3873065](http://ubuntuforums.org/showthread.php?p=3873065#post3873065)

---

### Post by SilverAdder on 2007-12-04
Thank you! I will check that out

---

### Post by SilverAdder on 2007-12-04
Well i found a solution! As stated by GSF1200S, in the other thread, the problem is with the refresh rate. I.e. in warsow i enabled vsync and it went away. My native refresh rate is 61Hz but now it is at 60Hz. So I tried changing the xorg.conf file the way it was described in the other thread but that made everything worse... My resolution locked to something horible and 3D acceleration was disabled. Any other way to do that, or did i just do something wrong?

---

### Post by GSF1200S on 2007-12-04
> **SilverAdder said:**
> Well i found a solution! As stated by you, GSF1200S, in the other thread, the problem is with the refresh rate. I.e. in warsow i enabled vsync and it went away. My native refresh rate is 61Hz but now it is at 60Hz. So I tried changing the xorg.conf file the way it was described in the other thread but that made everything worse... My resolution locked to something horible and 3D acceleration was disabled. Any other way to do that, or did i just do something wrong?

Failsafe X just kicked in. Whenever X fails to load on ati/nvidia drivers, it automatically reverts to open source drivers, which lack proprietary 3d code, and often times get the resolution wrong. Basically, when you changed the refresh rate X crashed, and the system reverted to open source drivers. Open back up your xorg.conf, change the refresh rate to 61, and restart X, and you should at least have 3d accel and the correct resolution while we try to figure this one out. While your at it, could you post the contents of xorf.conf here?

---

### Post by SilverAdder on 2007-12-04
I got it up and running fine again. Not the first time X has crashed on me :) my xorg.conf file looks like this: 

```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dk"
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
	Option		"HorizEdgeScroll"	"0"
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
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1680x1050" "1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

Since i dont have the refresh rate line i just added it under the "Screen" section, hoping it would work... I guess it didnt :)

---

### Post by GSF1200S on 2007-12-04
Mines nvidia, but take a look at mine- youll notice my refresh rate is listed under Section "Monitor"- I think you should try it there...

```
# xorg.conf (xorg X Window System server configuration file)

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
	Option		"HorizEdgeScroll"	"0"
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
	Identifier	"nVidia Corporation G70 [GeForce Go 7600]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-84
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce Go 7600]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1680x1050"
                                "800x600"
                                "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection

```

---

### Post by SilverAdder on 2007-12-04
Well this time it starts up fine. But when i look in "screen resolution" in system -> preferences it shows 60Hz and i cant choose 61Hz

EDIT: On a side note, the list of resolutions in "screen resolution" doesn't reflect the resolutions that are listed in xorg.conf. In the .conf i have 10280x1024 and i added 1650x1080. but i can also choose lower, like 1024x768, 800x600 and a few others. Dont know if it is of importance.

---

### Post by GSF1200S on 2007-12-04
> **SilverAdder said:**
> Well this time it starts up fine. But when i look in "screen resolution" in system -> preferences it shows 60Hz and i cant choose 61Hz

Ughh... strange.. Does ati give you any configuration panel or anything? We have one, and it does allow for the adjustment of the refresh rate.. It sucks because I know video driver and xorg stuff related to nvidia, but I know very little about ATI in particular. I actually have an x200m on a old laptop- I think I need to dig it out... let me dig a little and see if I can figure anything out..

---

### Post by SilverAdder on 2007-12-04
there is the ati catalyst control panel but in there is says 60Hz as well

---

### Post by GSF1200S on 2007-12-04
> **SilverAdder said:**
> there is the ati catalyst control panel but in there is says 60Hz as well

Take a look at these:

[http://ubuntuforums.org/showthread.php?t=474287](http://ubuntuforums.org/showthread.php?t=474287)
[http://ubuntuforums.org/showthread.php?t=125904](http://ubuntuforums.org/showthread.php?t=125904)

and then the screen shot which shows what mine is.. I dont know about that Screen Resolution GUI as I dont have it.. but xorg.conf should take precedence over anything else. The fact that the refresh rate isnt varied is almost certainly youre problem, but now you need to know the monitors vertical and horizontal refresh rates and input them in the xorg as they are in mine. Hopefully a dev or a guru can tell us what the precedence is in Ubuntu. I know ive heard that in some distros, the GUI settings will actually OVERRIDE manual entrys  in a text config file, but I cant see that being the case here.. Ill keep watching this thread and hopefully we can eventually get you somewhere (i felt your pain as I said before)

Good Luck!

**EDIT** You see that in BOTH of those threads manually editing the xorg with proper refresh rates fixed the problem.. so I would try to find out that info on your monitor (maybe a google search on the brand?) and input those values. Have patience- video card drivers, especially for ati are on of the hardest things to conquer it seems..

---

### Post by SilverAdder on 2007-12-04
Maybe its because the horizontal refresh isn't configured? Ill take a look at those threads and see if a cant get this to work properly.

---

### Post by SilverAdder on 2007-12-04
I cant for the life of me find the horiz and vert information for my laptop anywhere! My laptop is an Acer Ferrari 5000, if anyone knows the info or knows where to look please let me know.

---

