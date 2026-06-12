---
title: "[SOLVED] Enabling DVI"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by fizur2002 on 2008-02-06
Complete Noob at setting this up, had it working at one point, but something happened and can not for the life of me get it fixed.  LG L226WTQ-BW 22" monitor on a 8800GTX.  Ubuntu 7.10.  Be detailed and yet use laments terms so i can set it up easily.

---

### Post by talsemgeest on 2008-02-06
Ok first of all, what exactly do you want?

---

### Post by fizur2002 on 2008-02-06
i dont want to use the VGA connection, i want to use DVI so i dont have to play the cable switching game.

---

### Post by talsemgeest on 2008-02-06
Well on my box all that I have to do is plug in the DVI and the signal comes through it. If that doesnt work, change the settings in "screens and graphics", and lastly edit your xorg.conf

Hope this helps

---

### Post by fizur2002 on 2008-02-06
i dont know how to edit the config.. like i said, im completely new to this.

---

### Post by talsemgeest on 2008-02-06
OK, type: ```
gksudo gedit /etc/X11/xorg.conf
``` into the terminal and then enter your password. Your xorg.conf has most of the options for you display in it, but be careful when editing it

---

### Post by fizur2002 on 2008-02-06
what do i change things too?

---

### Post by talsemgeest on 2008-02-06
Look for some stuff about the monitor, and the craphics card and then change whatever looks right. Im sorry but I just cant help you more than that without seeing your xorg.conf

---

### Post by fizur2002 on 2008-02-06
here is my config file.

---

### Post by fizur2002 on 2008-02-06
i got the DVI to work using twinview but that came to an abrupt end when i went to fullscreen on a movie, when i rebooted, got the same black screen i always get when booting with the DVI cable.

---

### Post by LowSky on 2008-02-06
what are your computers complete specs?

what version of ubuntu are you using? 32 bit or 64 bit?

On my PC DVI just works, first off dont plug in differnet cables, just use one or the other. Also check your monitor settings see if it is set up to take DVi automatically

I dont know about you but VGA and DVI look identical to me. sure DVI can be used with HDMI but your taking about a regular computer monitor.

---

### Post by fizur2002 on 2008-02-06
Q6600
2GB ddr2
Asus P5K-E/Wifi-app
8800GTX
850watt PSU
LG 22"

The reason i want to use DVI is because i use it for windows as well, and VGA it has issues on linux and wont line up the screen properly, even when i use manual settings.  And this is 64bit

---

### Post by Perfect Storm on 2008-02-06
I have gtx 8800 as well on 64-bit and use Xerox 22" monitor, it pick it up automatically.

My xorg.conf if it helps,

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "dk"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "nVidia Corporation G80 [GeForce 8800 GTX]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       28-84
        Vertrefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G80 [GeForce 8800 GTX]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1680x1050"     "1280x1024"     "1280x854"     "1200x800"       "800x600"       "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
EndSection
Section "Module"
        Load            "glx"
EndSection

```

---

### Post by fizur2002 on 2008-02-06
so how would i graft that into mine so it does DVI automatically, because i cant really tell when im booting as there is no ubuntu splash screen.

---

### Post by Perfect Storm on 2008-02-06
Did you have screen when using the non-dvi way?

---

### Post by Shadowmeph on 2008-02-06
Hello I am also new to linux and although my problems are a little different I tried the command you posted for xorg.conf and it came up totally blank lol I know this is wrong so is there a way to fix this

---

### Post by Perfect Storm on 2008-02-06
linux is case sensitive, so big letters have to be big letters and low letters have to be low letters

---

### Post by Shadowmeph on 2008-02-06
I copied and pasted this into the terminal gksudo gedit /etc/X11/xorg.conf

---

### Post by bwtranch on 2008-02-06
You have to open the file from a terminal with an editor like gedit or nano or something like this example:

sudo gedit /etc/X11/xorg.conf

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
	Load  "GLcore"
	Load  "v4l"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "Monitor"
	Identifier   "Failsafe Monitor"
	VendorName   "Plug 'n' Play"
	ModelName    "Plug 'n' Play"
	Gamma        1
	ModeLine     "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
	ModeLine     "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
	ModeLine     "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
	ModeLine     "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
	ModeLine     "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
	ModeLine     "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
	ModeLine     "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	ModeLine     "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
	ModeLine     "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
	ModeLine     "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
	ModeLine     "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
	ModeLine     "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
	ModeLine     "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
	ModeLine     "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	ModeLine     "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	ModeLine     "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
	ModeLine     "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	ModeLine     "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
	ModeLine     "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
EndSection

Section "Monitor"
 #              
	Identifier   "monitor1"
	VendorName   "Generic LCD Display"
	ModelName    "LCD Panel 1440x900"
	HorizSync    31.5 - 56.0
	VertRefresh  56.0 - 65.0
	Gamma        1
	ModeLine     "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
	ModeLine     "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	ModeLine     "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
	ModeLine     "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
	ModeLine     "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
	ModeLine     "1440x900@60" 106.5 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
EndSection

Section "Monitor"

---

### Post by Shadowmeph on 2008-02-06
thanks peeps I didn't expect any replys so quickly and made a new post [http://ubuntuforums.org/showthread.php?p=4282721&posted=1#post4282721]("http://ubuntuforums.org/showthread.php?p=4282721&posted=1#post4282721")
Sorry about that if you still want to help me please come :)

---

### Post by bwtranch on 2008-02-06
Yeah, that's Ok. But, just so you know, bumping in less than 24 hrs. is highly frowned upon. It can even get you banned if you make a habit of it. But, back to the issue, post the output of the x file as previously stated. Be careful with this one. If you break it, you will be stuck with the command line and something tells me you're not quite ready for that!:)

---

### Post by Shadowmeph on 2008-02-06
> **bwtranch said:**
> Yeah, that's Ok. But, just so you know, bumping in less than 24 hrs. is highly frowned upon. It can even get you banned if you make a habit of it. But, back to the issue, post the output of the x file as previously stated. Be careful with this one. If you break it, you will be stuck with the command line and something tells me you're not quite ready for that!:)

is this what you are looking for?
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
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
	Identifier	"ATI Technologies Inc R420 JK [Radeon X800]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"L1752T"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R420 JK [Radeon X800]"
	Monitor		"L1752T"
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

### Post by bwtranch on 2008-02-06
I'm sorry. I don't know enough about this to say anything intelligent. I don't see anything wrong with the file. You could run the

sudo dpkg-reconfigure -phigh xserver-xorg

and see what you get (scary) well, not that bad. I would try it on my machine, but I don't want to break my xserver! There are some xconfig utilities out there, but I've never had much luck with them. This part is out of my field, maybe someone else can chime in.

---

### Post by fizur2002 on 2008-02-06
when using the regular vga, the monitor actually goes into power saving mode for a few seconds and then the login window will pop up.  on DVI it stays powered up and nothing will come up even after an hour.

---

### Post by wesley_of_course on 2008-02-06
Don't know if this would help , ( sorta,kinda , maybe ) ,  but found this ; 
  [https://answers.launchpad.net/ubuntu/+question/8045](https://answers.launchpad.net/ubuntu/+question/8045)
          Could you post your results from running this command ?
  This is a shot in the dark for me !
> grep NVIDIA /var/log/Xorg.0.log
                     If fixed , how ?  Would like to know. Thanks

---

### Post by talsemgeest on 2008-02-06
Is 1680x1050 your monitors native resolution?

---

### Post by fizur2002 on 2008-02-06
yes, it is my native resolution. 1680x1050 at 60hz

---

### Post by fizur2002 on 2008-02-07
DVI still will not work properly.

---

### Post by talsemgeest on 2008-02-07
Can you choose the closest thing to your monitor (i.e. not the generic lcd) in the "screens and graphics" menu? 
Thats about the only thing that I can think of right now I'm afraid.

---

### Post by fizur2002 on 2008-02-07
unfortunatly, in the list of monitors, LG has a very very small selection available, and none are what my monitor are.

---

### Post by talsemgeest on 2008-02-07
Find the closest one to yours. Do a little bit of research and find out which one uses only DVI, and then try selecting that

---

### Post by MarkX on 2008-02-07
Is there a DVI option in the setup menu of your actual monitor (the buttons on the front of it) ?

I have one with either BNC or normal input and have to switch between them (quite useful because I can run two computers on one monitor simultaneously).

---

### Post by fizur2002 on 2008-02-07
when trying to use DVI, i have the monitor in digital mode, and i know its in the correct mode because it says, "Digital".

---

### Post by fizur2002 on 2008-02-07
We can close this matter, as i am selling my 8800GTX and purchased me a 3870 today.  I hooked up the DVI and booted up Ubuntu.  My spash screen was there, it loaded up beautifully on DVI with no problems at all.  ATi FTW.

---

### Post by talsemgeest on 2008-02-07
Good to hear it! Don't forget to mark this thread as "solved"

---

### Post by fizur2002 on 2008-02-07
how do i mark it as solved?

---

### Post by talsemgeest on 2008-02-08
Its under the "thread tools" near the top of the page. You are supposed to do it  whenever its solved.

---

