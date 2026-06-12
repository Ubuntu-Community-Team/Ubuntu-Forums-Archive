---
title: "Stuck with 640x480 resolution"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by darkchest on 2007-01-19
I installed the nvidia drivers bcos of the 3dgame "scorched".  When i followed instructions and finished, i was stuck with only 640x480 resolution as the options.  I have checked /etc/X11/xorg.conf and the options that were in the "Screen" section were

********************************
Section "Screen"
Identifier "Default Screen"
Device "Generic Video Card"
Monitor "VG150"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "720x400" "640x480"
EndSubSection
.......
*******************************

I dont know what i havent done, or what i am meant to do.

PS.  My board is amd64

---

### Post by shareMenaPeace on 2007-01-19
I came along this problem too while running the game starcraft.
I modified the xorg.conf aswell but did something wrong.
Just watch out if you edit it. Make a backup if you edit it or you will end up with a non booting system (Command line works). And i had to use the live cd and root and mount the ubuntu partition in order to put the backup there.


And still starcraft doesnt run fullscreen here, pretty annoying. (My gfx card just offers 1 screen resolution).

---

### Post by reverseninja on 2007-01-19
What kind of monitor do you have?  Is the horizontal and vert refresh info correct in your xorg.conf?  I'd say post what your xorg.conf is so's we can's check's it's outseses.

---

### Post by darkchest on 2007-01-19
I have a ViewSonic ViewPanel VG150.  From what i Googled, i have a 60Hz refresh rate.  This is what is shown in the xorg.conf
*********************************************
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
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
	Load	"type1"
	Load	"vbe"
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
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"PCI:0:5:0"
EndSection

Section "Monitor"
	Identifier	"VG150"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"VG150"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
***************************************************

This is what the xorg.conf says

---

### Post by darkchest on 2007-01-19
This problem just started when i installed the nvidia driver.  It was working fine before.

---

### Post by SebMKd on 2007-01-19
Try this: [http://ubuntuforums.org/showthread.php?t=156243](http://ubuntuforums.org/showthread.php?t=156243)
Dee.dw has made a small GUI to edit your Xorg.conf. Plus he is very responsive to posts in this thread. The lastest version of Xorg-Edit let you try settings before saving!

It worked fine for me. I was stuck also with only one refresh rate available!

Good luck!:cool:

---

### Post by punx45 on 2007-01-19
check out [this extensive guide]("https://help.ubuntu.com/community/Latest_Nvidia_Dapper#head-740b39fc65fe970ba78e1f47496b2f1fb94bfacb-2") (dapper only, sorry) on the latest nvidia drivers.  i had some struggles with my nvidia card too.   this guide helped alot.

if you card is on this list then you need to install the legacy driver.
 ```
RIVA TNT 0x0020
RIVA TNT2/TNT2 Pro 0x0028
RIVA TNT2 Ultra 0x0029
Vanta/Vanta LT 0x002C
RIVA TNT2 Model 64/Model 64 Pro 0x002D
Aladdin TNT2 0x00A0
GeForce 256 0x0100
GeForce DDR 0x0101
Quadro 0x0103
GeForce2 GTS/GeForce2 Pro 0x0150
GeForce2 Ti 0x0151
GeForce2 Ultra 0x0152
Quadro2 Pro 0x0153
```

to figure out which card you have if you dont know:
```
lspci | grep VGA
```
or
```
lspci | grep -i nvidia
```

or if that doesn't work for some reason just lspci and look for it

---

### Post by shareMenaPeace on 2007-01-19
> lspci | grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 01d7 (rev a1)


I had to install the nvidia settings and did some install cmds to run openarena,  i dont remember the cmd now :)
But before (since ubuntu install) and after i just got 1 mode
> 
Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    SubSection     "Display"
        Depth       1
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x800"
    EndSubSection
EndSection
When i boot a NVIDIA screen is now visible.

---

### Post by darkchest on 2007-01-19
I installed the "xorg.conf editor", but i dont know which option i should change to let me get a higher resolution option.  I have changed the mode under the Screen tab to 1028x768, but it still doesnt work

---

### Post by darkchest on 2007-01-19
well after editing the xorg.conf.  I decided to restart the computer, and to my suprise it returned to normal.  Thanks everybody.  I actually dont know what i changed to rectify, but i rebooted to windows first then restarted and returned back to ubuntu.

THank you all.

---

### Post by punx45 on 2007-01-23
yeah, that is because after you make any changes in xorg.conf you need to restart X so it can read and apply the changes.   you could have achieved the same result by switching to a terminal with Alt+F1 and then (if using gnome)```
sudo /etc/init.d/gdm restart
```
a Ctl+Alt+Del would probably work to restart gnome too, unless you have that disabled.

---

