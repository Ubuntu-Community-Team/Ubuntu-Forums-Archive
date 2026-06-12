---
title: "HELP - screen resolution"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by nolagirl05 on 2006-08-20
I have read a lot on this topic, but since I am still fairly new to Ubuntu, I am afraid that I will try to do something unnecessary and mess it all up.  Here's what I know so far:

I tried to install Dapper 6.06 and got an error that said "Failed to start the X server" and then "fatal server error:  no screens found."  So I installed Dapper Beta from a Live CD, then upgraded to Dapper 6.06.  My monitor is working, but the only screen resolution option I have is 640 x 480 @ 85 Hz.  There are two other modes in my /etc/X11/xorg.conf file, but it only gives me the 640 x 480 option in the screen resolution menu.  

I tried to erase the 640 x 480 option in the xorg.conf file, leaving only the other two choices, but it didn't change anything.  

I also tried to change my horizontal and vertical refresh rates using "dpkg-reconfigure xserver-xorg."  After I made the changes, it gave me the "no screens found" error again and I had to start all over again by reinstalling Dapper.  Since I do not want to do that again, I am posting everything here before I make any more changes.

Thanks in advance for any help.  This is driving me NUTS.  It's hard to navigate because everything is so big that a lot of things are pushed off of my screen.  Please let me know if I need to post any other info.

Here are the tech specifications for my monitor:  [http://h10032.www1.hp.com/ctg/Manual/c00213493.pdf](http://h10032.www1.hp.com/ctg/Manual/c00213493.pdf)

Here is my /etc/X11/xorg.conf file:

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
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"hp mx704"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"hp mx704"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
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

---

### Post by Perfect Storm on 2006-08-20
Try this:

```
sudo nano /etc/X11/xorg.conf
```
add:

in Monitor section 


[b]HorizSync 30 - 70
VertRefresh 50 - 140[/b]

So it says:

```

Section "Monitor"
Identifier "hp mx704"
HorizSync 30 - 70
VertRefresh 50 - 140
Option "DPMS"
EndSection

```
Save and exit, reboot.

---

### Post by nolagirl05 on 2006-08-20
I made these changes and rebooted, but it is still at 640 x 800 @ 85 Hz, and there are no other choices in the screen resolution menu.

---

### Post by zxee on 2006-08-20
Are you saving the changes in nano? It's a easy mistake to make-just want to be sure. Also be sure that you are opening up xorg.conf and not a backup.
I don't know what else could be the problem. The driver is correct for your card. The default depth is set to 16. You could change that to 24 but I don't know that that would accomplish anything.
You may have to try the dpkg-reconfigure command again. 
You do not need to re-install if you get a broken xserver-you can run the command from the commandline and try again to set it up.

---

### Post by nolagirl05 on 2006-08-20
I am saving the changes...I reopened the file after I saved and closed just to make sure.  I know that it's the right file also.

I have run dpkg-reconfigure over and over.  Even when I change the settings there, it doesn't change anything.

Any other ideas?  This is so frustrating!

---

### Post by nolagirl05 on 2006-08-20
I have tweaked my xorg.conf file a few times so now it looks like this: 

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
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"hp mx704"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-140
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"hp mx704"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600"
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

I am still in 640 x 480 even though it isn't even listed as an option in my xorg.conf file.  How can that be?  Is there any other way to set screen resolution?  Maybe it's getting screwed up when I boot?  Maybe there's an old file that isn't being written over or something?  ](*,)

---

### Post by nolagirl05 on 2006-08-20
ALSO my Xorg log file says this:

(II) I810(0): hp mx704: Using hsync range of 30.00-70.00 kHz
(II) I810(0): hp mx704: Using vrefresh range of 50.00-140.00 Hz
(II) I810(0): Not using mode "1280x1024" (no mode of this name)
(II) I810(0): Not using mode "1024x768" (no mode of this name)
(II) I810(0): Not using mode "800x600" (no mode of this name)
(II) I810(0): Increasing the scanline pitch to allow tiling mode (640 -> 1024).
(--) I810(0): Virtual size is 640x480 (pitch 1024)
(**) I810(0):  Built-in mode "640x480"
(II) I810(0): Attempting to use 85.01Hz refresh for mode "640x480" (841)
(--) I810(0): Display dimensions: (320, 240) mm
(--) I810(0): DPI set to (50, 50)

---

### Post by bodhi.zazen on 2006-08-20
Not sure if this will help, just a guess.  I used to run the samme card (i810)

In Ubuntu the best defalult depth for me with this care was "16" so you are OK there.

Are you sere the vertical and horizontal refresh rates are correct for this monitor? If so my only other thought is to comment out " Load "glx" " so it looks like this:
```
# Load "glx"
```

---

### Post by nolagirl05 on 2006-08-20
Thanks for the response, but this did not change anything.

This is exasperating.

---

### Post by bodhi.zazen on 2006-08-20
Try modifying your
```
Depth 16
Modes "1280x1024" "1024x768" "800x600"
EndSubSection
```

to read
```
Depth 16
Modes "1600x1200" "1280x1024"
EndSubSection
```

---

### Post by nolagirl05 on 2006-08-21
Somebody suggested that this might be a bug.  The fix is here:

[https://bugs.freedesktop.org/show_bug.cgi?id=643](https://bugs.freedesktop.org/show_bug.cgi?id=643)

The problem is that I am too inexperienced to figure out exactly how to change my xorg-conf file to fix the problem.  Can anyone help me figure it out?

---

### Post by bodhi.zazen on 2006-08-21
nolagirl05:

I am not sure what you are asking.

To edit your xorg.conf:
```
 sudo nano /etc/X11/xorg.conf
```

To paste: Highlight the desired text to paste.

Place mouse in nano.

Hit middle mouse button.

---

### Post by nolagirl05 on 2006-08-21
"The desired text" is what I'm not sure about.  I don't know exactly which parts of that example I am supposed to cut and paste into my file.  I assume that most of my file will stay the same.

---

### Post by nalmeth on 2006-08-21
I've heard resolution problems with intel cards can be fixed with the i810resolution or i910resolution programs.

Problem is, I can't seem to find any info about them off hand. Will post here if I do.

---

### Post by nalmeth on 2006-08-21
ahh, I had the title wrong. It's 915resolution.
See a package description here:
[http://packages.ubuntu.com/dapper/x11/915resolution](http://packages.ubuntu.com/dapper/x11/915resolution)

Hopefully this helps

---

### Post by bodhi.zazen on 2006-08-21
> **nolagirl05 said:**
> "The desired text" is what I'm not sure about.  I don't know exactly which parts of that example I am supposed to cut and paste into my file.  I assume that most of my file will stay the same.

nolagirl05:

I am willing to help you, but I do not understand what you are fixing. What is the "The desired text"?

Could you explain your problem and post your xorg.conf? I looked at your link and the xorg.conf file I looked at is for dual monitors.

Perhaps you should start a separate thread? 

xorg.conf can be thought of as several sections. It is unlikely you will change these sections:
```

Section "Files"
Section "InputDevice"
Section "Monitor"

```

This leaves sections:
```

Section "ServerLayout"
Section "ServerFlags"
Section "Module"
Section "Modes"
Section "Device"
Section "Screen"
Section "DRI"
```

Unless you are using dual monitors, the xorg.conf at

[https://bugs.freedesktop.org/attachment.cgi?id=3502](https://bugs.freedesktop.org/attachment.cgi?id=3502)

will not help much.

This leaves:
```

Section "Modes"
Section "Screen"
```

Just a guess.

BACK UP YOUR xorg.conf BEFORE YIOU EDIT

---

### Post by nolagirl05 on 2006-08-28
All I know is somebody on another message board had the same exact problem as mine with the same monitor, and the bug fix I posted above supposedly worked.

I made some changes to my xorg.conf file based on the bug fix.  I did not get an X server failure error.  But I am still in 640x480@85 MHz.  There are still no other options in my screen resolution menu.  I am starting to think that I will not be able to fix this problem.

Here is my current xorg.conf file:

Section "Files"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
# path to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
# Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
Identifier "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
Driver "i810"
BusID "PCI:0:2:0"
EndSection

Section "Monitor"
Identifier "hp mx704"
Option "DPMS"
HorizSync 31.5-57.0
VertRefresh 50-70
UseModes "Modes[0]"
EndSection

Section "Modes"
Identifier "Modes[0]"
Modeline "1280x1024@60" 108 1280 1328 1440 1688 1024 1025 1028 1066
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
Monitor "hp mx704"
DefaultDepth 16
SubSection "Display"
Depth 1
Modes "1280x1024" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
Mode 0666
EndSection

Thanks to everybody who is trying to help me out!

---

### Post by bodhi.zazen on 2006-08-28
nolagirl05:

thank you fro posting your xorg.conf

May I ask exaclty what monitor are you using?

From your modline I assume you know what you are doing, but....

Well it is not working for you.

Initial thoughts (I will have to think on the rest):

1. What type mouse are you using? If you have a mouse with a wheel, and the middle button is activated by pressing down,
In the mouse section change:

Option "Emulate3Buttons" "true"

to
Option "Emulate3Buttons" "false"

2. You can un-comment # Load "glx" since that did not fix your problem.

3. Simplify:

Change:

Identifier "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"

to:
# Identifier "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
Identifier "Intel"

in the "Device" and "Screen" sections.

Last, change
> Section "Monitor"
Identifier "hp mx704"
Option "DPMS"
HorizSync 31.5-57.0
VertRefresh 50-70
UseModes "Modes[0]"
EndSection

to:
```
Section "Monitor"
Identifier "hp mx704"
Option "DPMS"
HorizSync 30-70
VertRefresh 50-140
UseModes "Modes[0]"
EndSection
```

---

### Post by nolagirl05 on 2006-09-02
Sorry I haven't responded.  I am in law school, and classes just started again...so I have less time to work on this problem.  I will check in every few days.

OK, I changed my xorg.conf file again.  I did what has been suggested, and I also took out every mode in the "Screen" section except 1280x1024.  Here it is now:

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
	Option		"Emulate3Buttons"	"false"
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
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"hp mx704"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-140
	UseModes 	"Modes[0]"
EndSection

Section "Modes"
	Identifier "Modes[0]"
	Modeline "1280x1024@60" 108 1280 1328 1440 1688 1024 1025 1028 1066
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"hp mx704"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" 
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
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

I would like to point out that my log says this:  

(II) I810(0): Not using mode "1280x1024" (no mode of this name)
(II) I810(0): Increasing the scanline pitch to allow tiling mode (640 -> 1024).
(--) I810(0): Virtual size is 640x480 (pitch 1024)
(**) I810(0):  Built-in mode "640x480"
(II) I810(0): Attempting to use 85.01Hz refresh for mode "640x480" (841)

There are still no other options in my screen resolution menu except 640x480@85.  

My monitor is the HP Pavilion mx704.  I am not using dual monitors.

---

### Post by bodhi.zazen on 2006-09-03
Sorry you are still having problems.

I do not see any obvious problem.

? Thoughts would be- Where did you get that modline from?

If you know what you are donig OK, if not let's get rid of it for now.

Change:
> Section "Monitor"
Identifier "hp mx704"
Option "DPMS"
HorizSync 30-70
VertRefresh 50-140
UseModes "Modes[0]"
EndSection

Section "Modes"
Identifier "Modes[0]"
Modeline "1280x1024@60" 108 1280 1328 1440 1688 1024 1025 1028 1066
EndSection

to:
```
Section "Monitor"
Identifier "hp mx704"
Option "DPMS"
HorizSync 30-70
VertRefresh 50-140
# UseModes "Modes[0]"
EndSection

# Section "Modes"
# Identifier "Modes[0]"
# Modeline "1280x1024@60" 108 1280 1328 1440 1688 1024 1025 1028 1066
# EndSection
```

Seems obvious, but rember to re-start X once you have changed xorg.conf
Easiest way is Ctrl-Alt-Backspace.

If that fails, lets start over.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.Not_working
sudo dpkg-reconfigure -phigh xserver-xorg
```

Re-start X.

If that works consider yourself lucky.

If not open you new xorg.conf and edit the monitor section to look like this:
```
Section "Monitor"
Identifier "hp mx704"
Option "DPMS"
HorizSync 30-70
VertRefresh 50-140
EndSection
```

And again reduce your color depth in the "screen section"
```
Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
Monitor "hp mx704"
**DefaultDepth 16**
SubSection "Display"
Depth 1
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024"
EndSubSection
EndSection
```

Re start X.

If that fails, repost your new xorg.conf

---

### Post by EvilDan on 2006-09-04
I've just been reading this thread as I've had similar problems- resurrected an old Shuttle and couldn't get Ubuntu to give me any resolutions other than 640x480 regardless of what I was changing.

This may or may not help, but after some thrashing about tweaking things I noticed my Xorg log mentioned it was using my old backed-up copy in /home/[username]/ rather than the /etc/... one. Removed the backup and it started paying attention.

---

### Post by bakert on 2006-09-04
Don't fear editing your xorg.conf.  Take a copy with

```
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

(or use another name for the backup file if you like, as long as you remember it.)

Then if you get get the "no screens found" error instead of reinstalling Dapper you can do this:

```
$ sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

and you will be back to 640x480 to battle anew!

---

### Post by nolagirl05 on 2006-10-01
> **EvilDan said:**
> I've just been reading this thread as I've had similar problems- resurrected an old Shuttle and couldn't get Ubuntu to give me any resolutions other than 640x480 regardless of what I was changing.

This may or may not help, but after some thrashing about tweaking things I noticed my Xorg log mentioned it was using my old backed-up copy in /home/[username]/ rather than the /etc/... one. Removed the backup and it started paying attention.

I was really hoping this was the case because it makes sense.  No matter what I do, it doesn't accept anything new.  But I checked my log, and it is supposedly using the correct file.

I am going to try some of the other suggestions now.

---

### Post by nolagirl05 on 2006-10-01
I have tried everything suggested in this thread, and nothing works.  What the crap is going on here?

Here is my current xorg.conf:

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
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"hp mx704"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-140
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"hp mx704"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
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

---

### Post by bodhi.zazen on 2006-10-01
I am sorry, this thread is 3 weeks old and I have nor re-read 3 pages worth of posts.

My only other thought is to install a new video driver.

[follow this thread](http://ubuntuforums.org/showthread.php?t=259437)

If that does not work perhaps your hardware is not supported.

[Ubuntu Hardware support](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by nolagirl05 on 2006-10-01
> **bodhi.zazen said:**
> I am sorry, this thread is 3 weeks old and I have nor re-read 3 pages worth of posts.

My only other thought is to install a new video driver.

[follow this thread](http://ubuntuforums.org/showthread.php?t=259437)

If that does not work perhaps your hardware is not supported.

[Ubuntu Hardware support](https://wiki.ubuntu.com/HardwareSupport)

When I tried to do this, it told me to manually edit my "/etc/default/915resolution" file based on the modes listed in "915resolution -l".  I tried to do this, but it did not work.

Maybe I'll go post on the other thread and see if someone can help me.

---

### Post by mips on 2006-10-01
Maybe have a look in the Hardware->Video forum.

I'm off to bed   ZZZZZzzzzzzzz

---

### Post by bodhi.zazen on 2006-10-02
> **nolagirl05 said:**
> When I tried to do this, it told me to manually edit my "/etc/default/915resolution" file based on the modes listed in "915resolution -l".  I tried to do this, but it did not work.

Maybe I'll go post on the other thread and see if someone can help me.

Try this link and let me know how it goes:

[Bodhi's Monitor How-to](http://ubuntuforums.org/showthread.php?t=269052)

If you have probmes, error message ?

---

### Post by nolagirl05 on 2006-12-17
> **bodhi.zazen said:**
> Try this link and let me know how it goes:

[Bodhi's Monitor How-to](http://ubuntuforums.org/showthread.php?t=269052)

If you have probmes, error message ?

I tried all of this.  No problems or error messages, but I am still stuck in one resolution with no other options in the menu.  I am trying to get 1024x768 @ 85 Hz because that is the ideal according to my monitor manual.

Here is my current xorg.conf:  

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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
	Identifier	"intel i915"
	Driver		"i810"
	VideoRam	8192
EndSection

Section "Monitor"
	Identifier	"hp pavilion mx704"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-140
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"intel i915"
	Monitor		"hp pavilion mx704"
	DefaultDepth	16
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

HERE IS MY /ETC/DEFAULT/915RESOLUTION FILE:

# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=45
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=1024
YRESO=768
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
BIT=16

---

### Post by halitech on 2006-12-17
if you run 

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

do you have the screen resolutions checked for 800x600 and 1024x768? I know when I was running it on an old ATI card it defaulted to just the 640x480 but after I ran it and selected the other resolutions, it worked fine

---

### Post by nolagirl05 on 2006-12-17
> **halitech said:**
> if you run 

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

do you have the screen resolutions checked for 800x600 and 1024x768? I know when I was running it on an old ATI card it defaulted to just the 640x480 but after I ran it and selected the other resolutions, it worked fine

Yes, I have the other resolutions checked and I don't have 640x480 checked.

---

### Post by painterboy on 2006-12-17
Well looks like im not the only one having this problem.  Im using the exact same chipset as you and experiencing the exact same difficulties. All i got to say is its frustrating as hell.  Heres my xorg.conf

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"DELL E773c"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"DELL E773c"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768" "800x600" "640x480"
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

---

### Post by bodhi.zazen on 2006-12-17
nolagirl05 and painterboy :

I am sorry you are having problems and I will try to help if I can.

I have two thoughts:

First add this line to your monitor section(s):
>         Option "UseEdidFreqs" "1"

like this:
```
Section "Monitor"
	Identifier	"Monitor2"
	VendorName	"IBM"
	ModelName	"IBM P202"
	HorizSync	30-107
	VertRefresh	50-160
        **Option "UseEdidFreqs" "1"**
	Option		"DPMS"
EndSection
```

My second thought is to update your BIOS.

---

### Post by painterboy on 2006-12-18
ok thanks ill try adding that.  Umm how would I update the Bios?

---

### Post by bodhi.zazen on 2006-12-19
First see if there is an update available (check with your manufacturer)

Google search <manufacturer> update BIOS

Try the > Option "UseEdidFreqs" "1" first 8)

---

