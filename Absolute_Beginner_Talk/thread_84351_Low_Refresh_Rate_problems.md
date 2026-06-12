---
title: "Low Refresh Rate problems"
date: 2005-10-30
forum: Absolute Beginner Talk
---

### Post by Animus on 2005-10-30
My refresh rate in Ubuntu seems to be stuck at around 60hz, and I was wondering if there was a way to make Ubuntu let me raise it, as it used to run higher in windows. I know both my monitor and graphics card will support a higher refresh rate, so does anyone know how I might go about changing that?

---

### Post by audax321 on 2005-10-30
You need to find the vertical/horizontal refresh rate for your monitor and then edit /etc/X11/xorg.conf

So in order for anyone to help you, please tell us what the manufacturer/model of your monitor is.

---

### Post by nitricacid on 2005-10-30
How do i find out the vertical/horizontal refresh rate?

I know my monitor can go to atleast 80-85refresh rate.

Here is what it says in my /etc/x11/xorg.conf

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

---

### Post by Animus on 2005-10-30
Well, I'm not exactly sure.  It's an old Dell OEM CRT, 17" screen Serial No. 5C54417UH0LN

I'm not sure if its an 0 or O.

Is there any way I can get the information you need through Ubuntu?

---

### Post by Animus on 2005-10-31
Bump!  C'mon, there must be a way to get this refresh rate up...

---

### Post by David Marrs on 2005-10-31
What are your monitor's  HorizSync & VertRefresh? They'll be in your monitor's manual or hopefully on the manufacturer's website. Presumably, you find out those values then put them in place of whatever's currently in your xorg.conf. Of course, I could be wrong, so backup your xorg.conf first.

---

### Post by Teroedni on 2005-10-31
To nitricacid
I have edited your xorg file 
You said your monitor could support 85 hz so i raised your horinzsync and vertrefresh rates. Then all should work better:)


Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-85
VertRefresh 43-90
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection

---

### Post by frodon on 2005-10-31
If you know the exact name of your screen (often written on your monitor) you could find the specification of your screen on internet. Also if you kept the box of your screen or if you kept the manual, the horizontal and vertical refresh rate parameters are specified in.

BE CAREFUL, wrong parameters could destroy your screen !

---

### Post by Animus on 2005-10-31
Nope, don't have the box or the manual, as I said, its a secondhand OEM Dell monitor.  There is no model or serial number on my monitor, just the typical "Dell" Logo...

The Serial is No. 5C54417UH0LN if that helps at all.  

Argh, I'm getting headaches from looking at the screen for any amount of time...

---

### Post by Animus on 2005-10-31
I really need some help here, can anyone think of any way to get the refresh rate up?

---

### Post by janne5011 on 2005-10-31
hi. first of all Im a  noob:) 
first
read this

[https://wiki.ubuntu.com/FixVideoResolutionHowto](https://wiki.ubuntu.com/FixVideoResolutionHowto)

if you still have windows look at your win settings and try to figure out if tehre is something u can use.
I got the same problems before, here is how my xorg.conf looks like now the relevant part:
Section "Monitor"
	Identifier	"MD9759AH"
	Option		"DPMS"
        HorizSync        60 <----this add yours
        VertRefresh     75<-----this add yours

try to get the right settings for your monitor Horisync and VertRefresh-

later take out all other settings I mean for example if yours is "1024x768"
remove 800x600 everywhre since it seems to change back else-
be catiuos edit that file it can screw up things
hope this helps...

---

### Post by frodon on 2005-10-31
If you have windows, you could see the exact name of your screen in  configuration panel > sytem.
If you get the hsync and vert sync parameters your problem is solved.
By the way, did you try this command ? : ```
sudo dpkg-reconfigure xserver-xorg
```It will reconfigure your display, if you're lucky it can work.

---

### Post by Animus on 2005-10-31
Configuring the xserver didn't do anything, and that guide seems more focused on changing the actual resolution of the screen...

Is there any way to figure out model information about my Monitor any other way?  I don't have windows, or a manual, or anything like that.  All I know is that it came with my old departed dell tower years ago.

---

### Post by Teroedni on 2005-11-01
Animus
Can you please post your xorg.conf file

Start terminal and paste this into it

sudo gedit /etc/X11/xorg.conf

then paste the textfile in here

---

### Post by heimo on 2005-11-01
Hi Animus!

What kind of monitor do you have? LCD, CRT? What size? 17", 19"? Do you kwow some specific mode it can run on? 1024x768@75Hz? 1280x1024@80Hz?
If reconfiguring doesn't help, you could make a custom modeline to your xorg.conf. Some examples:
 ```
# V-freq: 80.00 Hz  // h-freq: 86.05 KHz
Modeline "1280x1024" 167.97  1280 1368 1576 1952  1024 1024 1027 1075 
# V-freq: 75.00 Hz  // h-freq: 60.31 KHz
Modeline "1024x768" 81.54  1024 1064 1168 1352   768  768  770  804 
``` 

You may also need to edit VertRefresh and HorizSync lines. Probably the modelines are not even neccessary, but they give you information about correct horizsync values. Instructions how to do it and where to find more debugging information:
[http://www.ubuntuforums.org/showthread.php?t=83973]("http://www.ubuntuforums.org/showthread.php?t=83973")

---

### Post by Animus on 2005-11-03
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
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
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X800 XL (R430 UM)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-80
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon X800 XL (R430 UM)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
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


There's my file, thanks for helping so far guys

---

### Post by Teroedni on 2005-11-04
okay
There is several solution to solve this. I start with the easiest first:)


This is taken from your xorg.

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-80
VertRefresh 43-60
EndSection

Do your monitor support 1280x1024 @85herz?
if it does use the new section i post now 


Use this:

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-85
VertRefresh 43-110
EndSection

You see that i increased the values a bit. 
You should no be able to use 1280x1024 at 85herz

---

### Post by Teroedni on 2005-11-04
About you dell monitor 
In the back it should stand model number and such
or does it only states the serial number?

---

### Post by Animus on 2005-11-04
The Model Number is M991, manufactured July 2001.

---

### Post by janne5011 on 2005-11-04
[QUOTE=Animus]The Model Number is M991, manufactured July 2001.[/QUOTE]


Dell M991 - display - CRT - 19"
Manufacturer: Dell, Inc. 
Part number: M991 

Product Short Spec: 
Compatibility: PC 
Display (projector) technology: CRT 
Display (projector) diagonal size: 19 in 
Max resolution: 1600 x 1200 
Dot pitch: 0.26 mm

Max sync rate (V x H)	160 Hz x 96 KHz

link:
[http://reviews.cnet.com/Dell_M991___display___CRT___19_/4507-3175_7-31218545.html?tag=nav](http://reviews.cnet.com/Dell_M991___display___CRT___19_/4507-3175_7-31218545.html?tag=nav)

hope this helps ;)

---

### Post by Animus on 2005-11-04
Awesome, thanks a lot for looking that up.  Now I just hope somehere here can show me how to use it ^_^

---

### Post by frodon on 2005-11-04
Open your xorg.conf file and modify the monitor section like that : ```
Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
[B]HorizSync 30-96
VertRefresh 50-160[/B]
EndSection
```and then do a Ctrl + Alt + Backspace to restart X.

---

### Post by Animus on 2005-11-04
Sweet, its at 85 now, thanks a lot for your help!

---

### Post by Animus on 2005-11-04
I don't suppose anyone would happen to know how to make an icon for firefox?  I installed the new RC through the wikipedia guide, but I don't have an icon for it, and I have to open it via terminal, any thoughts?

---

### Post by DavidGX on 2005-11-13
Hey guys. I'm also having this problem. My monitor supports 1280x768 @ 75hz but I can only select 60hz. Luckily it's an LCD so no flicker but I would like to be able to use 75. The Monitor section of xorg.conf looks like:

Section "Monitor"
	Identifier   "W2600 LCD TV"
	HorizSync    35 - 60
	VertRefresh  50.0 - 60.0
	Option	    "DPMS"
EndSection

My tv is a Dell W2600 26" widescreen LCD monitor/hdtv. The horizontal/vert sync ranges weren't in the manual and I can't find them on dell.com or anywhere else =/

I haven't really tried guessing at them myself because I don't want to damage the monitor.

Anyone got any ideas?

---

### Post by Teroedni on 2005-11-13
try 65 on both should not destroy it:)

you could also use this modeline
Modeline "1280x768@75" 105.64 1280 1312 1712 1744 768 782 792 807

---

### Post by DavidGX on 2005-11-14
[QUOTE=Teroedni]try 65 on both should not destroy it:)

you could also use this modeline
Modeline "1280x768@75" 105.64 1280 1312 1712 1744 768 782 792 807[/QUOTE]

Modeline? Not familiar with that. Is that an option somewhere or a search term? (linux n00b here o_O)

---

### Post by Teroedni on 2005-11-14
post your xorg file and i show you;)

sudo gedit /etc/X11/xorg.conf

---

### Post by DavidGX on 2005-11-15
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # paths to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/CID"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load  "GLcore"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

#Section "InputDevice"
#	Identifier  "Configured Mouse"
#	Driver      "mouse"
#	Option	    "CorePointer"
#	Option	    "Device" "/dev/input/mice"
#	Option	    "Protocol" "ImPS/2"
#	Option	    "Emulate3Buttons" "true"
#	Option	    "ZAxisMapping" "6 7"
#EndSection

Section "InputDevice"
        Identifier	"Configured Mouse"
        Driver		"mouse"
	Option		"Protocol"		"evdev"
	Option		"Dev Name"		"Logitech USB-PS/2 Optical Mouse"
	Option		"Dev Phys"		"usb-*/input0"
        Option		"Device"		"/dev/input/event1"
	Option		"Buttons"		"10"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Monitor"
	Identifier   "W2600 LCD TV"
	HorizSync    35 - 65
	VertRefresh  50.0 - 65.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon 9800 XT (RV350 NJ)"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon 9800 XT (RV350 NJ)"
	Monitor    "W2600 LCD TV"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

---

### Post by Teroedni on 2005-11-15
in section monitor;)


```

Section          "Monitor"
Identifier        "W2600 LCD TV"
HorizSync       35 - 65
VertRefresh     50.0 - 65.0
Option           "DPMS"
Modeline        "1280x768@75" 105.64 1280 1312 1712 1744 768 782 792 807
EndSection

```

---

### Post by heimo on 2005-11-15
And you probably also need to change the upper limit of VertRefresh line (HorizSync should be fine)
```
 VertRefresh     50.0 - 75.0
``` 
EDIT: If 75 doesn't work, you may (at your own risk...) try 76.

 ```
Modeline "1280x768@75"     105.64  1280 1312 1712 1744    768  782  792  807
``` Results 75.06 refresh rate.

---

### Post by DavidGX on 2005-11-15
[QUOTE=Teroedni]in section monitor;)


```

Section          "Monitor"
Identifier        "W2600 LCD TV"
HorizSync       35 - 65
VertRefresh     50.0 - 65.0
Option           "DPMS"
Modeline        "1280x768@75" 105.64 1280 1312 1712 1744 768 782 792 807
EndSection

```[/QUOTE]

I tried that but when I rebooted I got no picture. Had to sudo nano and remove the line. I don't get it because I know my monitor can do 1280x768@75hz because that's the mode I used in windows.

---

### Post by DavidGX on 2005-11-15
[QUOTE=heimo]And you probably also need to change the upper limit of VertRefresh line (HorizSync should be fine)
```
 VertRefresh     50.0 - 75.0
``` 
EDIT: If 75 doesn't work, you may (at your own risk...) try 76.

 ```
Modeline "1280x768@75"     105.64  1280 1312 1712 1744    768  782  792  807
``` Results 75.06 refresh rate.[/QUOTE]

I have the VertRefresh set at 50.0 - 75.0 although I can't select 75hz from the screen resolution panel. I tried adding the modeline along side that and I couldn't get picture. Had to sudo nano and remove that. Left the VertRefresh at 75 though and it's working fine.. although I still can't select 75hz =/

---

