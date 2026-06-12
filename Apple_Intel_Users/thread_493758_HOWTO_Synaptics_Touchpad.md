---
title: "HOWTO: Synaptics Touchpad"
date: 2007-07-06
forum: Apple Intel Users
---

### Post by benanzo on 2007-07-06
**[SIZE="5"]HOWTO: Synaptics Touchpad[/SIZE]**

This tutorial provides information on how to enable the advanced features of the Synaptics touchpad on the MacBooks and Pros (and any other touchpad that uses the synaptics driver.)

Make sure the Synaptics driver and the graphical configuration program **gsynaptics** (for KDE use **ksynaptics** or **qsynaptics**) are installed:
```
sudo apt-get install xserver-xorg-input-synaptics gsynaptics
```

**NOTE:**  It is possible that the GUI applications (gsynaptics, qsynaptics, ksynaptics) for manipulating the touchpad settings will override the settings set manually in **/etc/X11/xorg.conf**.  If the parameters you set manually in **/etc/X11/xorg.conf** do not seem to take effect, try uninstalling the GUI application then restart the XServer (instructions below.)

Now we're going to configure the touchpad to utilize the Synaptics driver and it's advanced features:
```
sudo gedit /etc/X11/xorg.conf
```
First we need to add a section so X knows we've got a touchpad that uses the **synaptics** driver:
```

Section "InputDevice"
          Identifier "Synaptics Touchpad"
          Driver "synaptics"
          #...
          #...  *This area will contain the options we want to use with our touchpad*
          #...
EndSection

```
**NOTE:** If Xorg discovered your touchpad when it installed you might have this section already.  If that is the case you can skip to the part below about **Options**.

It doesn't matter where in the xorg.conf file you add this section, but it makes the most sense to just put it beneath the section for your keyboard or mouse.  You can find that area by pressing **CTRL-F** in gEdit and typing **kbd**.  That will instantly show this text (or similar):
```

Section "InputDevice"
          Identifier      "Generic Keyboard"
          Driver          "kbd"
          Option          "CoreKeyboard"
          Option          "XkbRules"      "xorg"
          Option          "XkbModel"      "pc105"
          Option          "XkbLayout"     "us"
EndSection

```
At the bottom of this block (after **EndSection**) paste the new block for the Synaptics Touchpad:
```

Section "InputDevice"
          Identifier      "Generic Keyboard"
          Driver          "kbd"
          Option          "CoreKeyboard"
          Option          "XkbRules"      "xorg"
          Option          "XkbModel"      "pc105"
          Option          "XkbLayout"     "us"
EndSection
[COLOR="DarkRed"]
Section "InputDevice"
          Identifier "Synaptics Touchpad"
          Driver "synaptics"
          #...
          #...  *This area will contain the options we want to use with our touchpad*
          #...
EndSection[/COLOR]

```
Next we need to add a line to the **ServerLayout** of our xorg.conf so that the touchpad is activated when we start X.  Do **CTRL-F** again and search for **ServerLayout**.  This will take you to a block of text that specifies the active X server devices:
```

Section "ServerLayout"
	Identifier	    "Default Layout"
        Screen              "Default Screen"
	InputDevice         "Generic Keyboard"
	InputDevice	    "Configured Mouse"
EndSection

```

(You might have lines that reference devices such as **wacom** and **eraser**.  For our purposes you can just ignore them along with their relevant **InputDevice** sections.)

We are going to add the Synaptics touchpad to the **ServerLayout**:
```

Section "ServerLayout"
	Identifier	    "Default Layout"
        Screen              "Default Screen"
	InputDevice         "Generic Keyboard"
	InputDevice	    "Configured Mouse"
[COLOR="DarkRed"]        InputDevice         "Synaptics Touchpad"[/COLOR]
EndSection

```
It doesn't matter what you call your devices so long as they are exactly the same as their relevant **Identifier** lines.  For instance, you can call your touchpad "MacBook Touchpad" instead of "Synaptics Touchpad" as long as the **Identifier** line in the **InputDevice** section above says "MacBook Touchpad" -- it doesn't matter what they are, so long as they're identical.

**NOTE:** It is suggested elsewhere that it's also required to add **Load "synaptics"** to **Section "Module"** in order for the touchpad to work.  However, I have never added that line and my touchpad has always worked.  In fact, the only difference I noticed when that line was added was a harmless (but annoying) error in my /var/log/Xorg.0.log file about it.  But nonetheless, if you experience trouble with X using your touchpad you can see if that fixes it.

OK, so now the infrastructure for adding functionality to our touchpad is in place.  Next we are going to define a few parameters to specify how the touchpad works.  Go back up to the **InputDevice** section we created for our touchpad.

**NOTE:** If you want to skip all the explanation mumbo-jumbo you can just scroll to the end and see a finished product.

We will replace these lines:
```

Section "InputDevice"
          Identifier "Synaptics Touchpad"
          Driver "synaptics"
          [COLOR="DarkRed"]#...
          #...  *This area will contain the options we want to use with our touchpad*
          #...[/COLOR]
EndSection

```
with **Options** that fine-tune how our touchpad operates.  The first few that we will add are **SendCoreEvents**, **Protocol**, **SHMConfig** and **Device**:
```

Section "InputDevice"
          Identifier "Synaptics Touchpad"
          Driver "synaptics"
          [COLOR="DarkRed"]Option "SendCoreEvents"          "True"
          Option "Protocol"                "auto-dev"
          Option "Device"                  "/dev/psaux"
          Option "SHMConfig"               "True"[/COLOR]
EndSection

```
**NOTE:** The **Device** option is only necessary if we have multiple touchpads or if we experience trouble with X discovering our touchpad, which is unlikely.  Also note that **/dev/psaux** might not be your device, so if you have trouble with that option try removing it.

The only other of these options that I should explain is **SHMConfig**.  This allows the synaptics driver to change configuration parameters without having to restart X.  This option is required in order to use the **gsynaptics** or **ksynaptics** graphical configuration applications.

The remainder of the **Options** are purely up to the user and their comfort with how the touchpad operates. If we go to **System -> Help and Support** and search for **man:synaptics** (no spaces) or do:
```
man synaptics
```
in a terminal we can read through all the wonderful possibilities the synaptics driver offers us. However, individually configuring each option can be an incredibly daunting task.  You need to restart your X server by logging out and  then hitting **CTRL+ALT+BACKSPACE** and then logging back in for the new settings to take effect.  This is required if you make manual changes to the xorg.conf file.  However, after this initial X server restart you will be able to use **gsynaptics**, **ksynaptics** or **qsynaptics** to configure your touchpad on-the-fly.  If you want more granular control over every little thing the touchpad does, you will have to fiddle with the **Options** manually and restart the X server whenever you want to test.

The values of the **Options** require either a boolean string as in "True" or "False" (1 or 0 can also be used) or an integer value that usually represents time in milliseconds or physical x,y coordinates on the touchpad.  For instance the options to enable horizontal and vertical two finger scrolling are either enabled or not.  So they request a boolean value:
```

        Option		"VertTwoFingerScroll"   "True"
	Option		"HorizTwoFingerScroll"  "True"

```
A specific value is required to define the size of the right edge (for scrolling) so it requests an integer value corresponding to the x coordinate on the touchpad:
```

Option          "RightEdge"     	"1100"

```
The maximum width (x) of the touchpad on a first-gen MacBook is 1200.  So the above value tells the synaptics driver that the space between 1100 and 1200 is reserved as the RightEdge for scrolling.  The maximum height (y) is 380.  (It is plain to see that the physical width is *not* actually more than 3x the height, but it works anyway.)

**NOTE:** There are multiple ways to convey a boolean value in any section of the xorg.conf file.  "True" can be expressed by any of the following: **on, true, 1, yes** and "False" can be: **off, false, 0, no**.  So don't be confused if you see these values used elsewhere.  The use of a boolean **Option** that has a built-in negative indication in the actual name of that **Option** such as **GuestMouseOff** should be exemplified:
```

Option          "GuestMouseOff"        "True"      # disables external mice
Option          "GuestMouseOff"        "False"     # enables external mice (default)

```
Here I provide a meager set of **Options** which work well on a first-gen MacBook:
```

Section "InputDevice"
          Identifier "Synaptics Touchpad"
          Driver "synaptics"
          Option "SendCoreEvents"          "True"
          Option "Protocol"                "auto-dev"
          Option "Device"                  "/dev/psaux"
          Option "SHMConfig"               "True"
          Option "LeftEdge"      	   "100"
	  Option "RightEdge"     	   "1100"
	  Option "TopEdge"       	   "50"
	  Option "BottomEdge"    	   "300"
	  Option "FingerLow"     	   "30"
	  Option "FingerHigh"    	   "40"
	  Option "MaxTapMove"              "100"
	  Option "TapButton1"    	   "1"
	  Option "TapButton2"    	   "3"
	  Option "TapButton3"    	   "2"
	  Option "MinSpeed"      	   "0.15"
	  Option "MaxSpeed"      	   "0.90"
	  Option "AccelFactor"   	   "0.10"
	  Option "VertScrollDelta"         "25"
	  Option "HorizScrollDelta"        "30"
EndSection

```

There are *plenty* more configuration possibilities (including scrolling by rotating your finger in a circle like on an iPod) that I wont go into right now.  I will return from time to time to add and explain more **Options**.  Stay tuned.

If you have awesome **Options** please post them!  It's all about the **Options**.

Good Luck!

---

### Post by grim1234 on 2007-07-06
To use the corners as mouse buttons rather using 2/3 fingers and pressing button :

```

	Option "Emulate3Buttons" "true"
	Option "RTCornerButton" "0"
	Option "RBCornerButton" "2"
	Option "LTCornerButton" "0"
	Option "LBCornerButton" "3"

```

1 = Left Button
2 = Middle Button
3 = Right Button

---------------------------------

To use two fingers to scroll like OSX :

```

	Option "VertTwoFingerScroll" "1"
	Option "HorizTwoFingerScroll" "1"

```

---

### Post by cyberdork33 on 2007-07-06
There is also some info here if you are having trouble:
[http://www.jasonparekh.com/linux-on-macbook/](http://www.jasonparekh.com/linux-on-macbook/)

---

### Post by jackiecanev2 on 2007-07-06
maybe i'm missing somehting, but why not just use qsynaptics? its got a nice gui and not a whole lot of xorg.conf editing to be done...

theres a guide here: [http://ubuntu1501.blogspot.com/2007/04/configure-synaptic-touchpad-settngs.html]("http://ubuntu1501.blogspot.com/2007/04/configure-synaptic-touchpad-settngs.html")

---

### Post by cyberdork33 on 2007-07-06
he does outline the use of gsynaptics, and ksynaptics, (IDK why qsynaptics wasn't included) but none of these configure all the options.

---

### Post by thully on 2007-07-06
I've experimented with options and have found the following to work best.  Someone posted them here a while back.

What they do is:

* corner tapping for right/middle buttons (as mentioned above)
* reasonably responsive two-finger scrolling (actually, more responsive than Windows in Boot Camp - but less so than OS X)

Just use this section for synaptics touchpad:

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "LeftEdge" "150"
Option "RightEdge" "1070"
Option "TopEdge" "100"
Option "BottomEdge" "310"
Option "FingerLow" "25"
Option "FingerHigh" "30"
Option "MaxTapTime" "180"
Option "MaxTapMove" "220"
Option "MaxDoubleTapTime" "180"
Option "HorizEdgeScroll" "0"
Option "VertEdgeScroll" "0"
Option "TapButton1" "0"
Option "TapButton2" "0"
Option "TapButton3" "0"
Option "LockedDrags" "off"
Option "VertScrollDelta" "20"
Option "HorizScrollDelta" "50"
Option "VertTwoFingerScroll" "1"
Option "HorizTwoFingerScroll" "1"
Option "MinSpeed" "1.10"
Option "MaxSpeed" "1.30"
Option "AccelFactor" "0.08"
Option "Emulate3Buttons" "true"
Option "SHMConfig" "on"
# corner buttons
Option "RTCornerButton" "0"
Option "RBCornerButton" "2"
Option "LTCornerButton" "0"
Option "LBCornerButton" "3"
EndSection

---

### Post by Gen2ly on 2007-07-06
Great tutorial, benanzo. I added it to the stickie.

---

### Post by Oliver Barker on 2007-07-08
lol, when i save it, it doesn't take effect, am i doing it wrong? i'm doing the tutorial correctly and then clicking save (on 7.04 is it helps)

---

### Post by cyberdork33 on 2007-07-08
you will have to reload Xorg. You can hit CTRL+ALT+BKSP to reset the server

---

### Post by kainrcir on 2007-07-12
I have a c2d 2nd gen macbook, and was initially having alot of problems with the touchpad sensing the presence of my finder, even with fingerhigh at 1.  Adding this line to the bottom of /etc/modprobe.d/options and rebooting fixed it:

options appletouch threshold=3

---

### Post by troseph on 2007-07-16
Ok. None of this has improved my mouse. Also when I use the two finger scrolling in firefox, it takes me back a page in the history in firefox.

My system is a black MacBook CoreDuo 2.0ghz

My xorg.conf section for the touchpad:

```

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "LeftEdge" "150"
Option "RightEdge" "1070"
Option "TopEdge" "100"
Option "BottomEdge" "310"
Option "FingerLow" "25"
Option "FingerHigh" "30"
Option "MaxTapTime" "180"
Option "MaxTapMove" "220"
Option "MaxDoubleTapTime" "180"
Option "HorizEdgeScroll" "0"
Option "VertEdgeScroll" "0"
Option "TapButton1" "0"
Option "TapButton2" "0"
Option "TapButton3" "0"
Option "LockedDrags" "off"
Option "VertScrollDelta" "20"
Option "HorizScrollDelta" "50"
Option "VertTwoFingerScroll" "1"
Option "HorizTwoFingerScroll" "1"
Option "MinSpeed" "1.10"
Option "MaxSpeed" "1.30"
Option "AccelFactor" "0.08"
Option "Emulate3Buttons" "true"
Option "SHMConfig" "on"
# corner buttons
Option "RTCornerButton" "0"
Option "RBCornerButton" "2"
Option "LTCornerButton" "0"
Option "LBCornerButton" "3"
EndSection

```

I also would like to say the corner buttons do not work either. Could it be becauce I am using an older intel macbook? I tried the configuration from the actual post, with less success.

---

### Post by benanzo on 2007-07-16
You restarted your X server after making the changes right?  Log out, hit CTRL-ALT-BACKSPACE, then log back in.

---

### Post by rodo-&gt;dave on 2007-07-16
Just wanted to say "Thanks benanzo!" great info I have been searching for.

---

### Post by cyberdork33 on 2007-07-16
> **troseph said:**
> Ok. None of this has improved my mouse. Also when I use the two finger scrolling in firefox, it takes me back a page in the history in firefox.

That is just firefox's weird default settings. I am sure you need to change something in about:config

---

### Post by troseph on 2007-07-17
> **benanzo said:**
> You restarted your X server after making the changes right?  Log out, hit CTRL-ALT-BACKSPACE, then log back in.

Yes. I actually rebooted the machine, and still jerky movement, no corner buttons, nothing works with the exception of the two finger scrolling. Is there something I might have missed? I'm starting to find the keyboard and touchpad to me very annoying in Ubuntu. 

Here is my xorg.conf maybe I missed something, but i almost doubt it.

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "LeftEdge" "150"
Option "RightEdge" "1070"
Option "TopEdge" "100"
Option "BottomEdge" "310"
Option "FingerLow" "25"
Option "FingerHigh" "30"
Option "MaxTapTime" "180"
Option "MaxTapMove" "220"
Option "MaxDoubleTapTime" "180"
Option "HorizEdgeScroll" "0"
Option "VertEdgeScroll" "0"
Option "TapButton1" "0"
Option "TapButton2" "0"
Option "TapButton3" "0"
Option "LockedDrags" "off"
Option "VertScrollDelta" "20"
Option "HorizScrollDelta" "50"
Option "VertTwoFingerScroll" "1"
Option "HorizTwoFingerScroll" "1"
Option "MinSpeed" "1.10"
Option "MaxSpeed" "1.30"
Option "AccelFactor" "0.08"
Option "Emulate3Buttons" "true"
Option "SHMConfig" "on"
# corner buttons
Option "RTCornerButton" "0"
Option "RBCornerButton" "2"
Option "LTCornerButton" "0"
Option "LBCornerButton" "3"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by mitchellsimon on 2007-07-17
I've got Ubuntu running on my Core Duo Macbook Pro (2.16) in dualboot with OS X. I have been trying to get the 2 finger scrolling working with the trackpad but adding these lines of code don't work.

The scrolling on the right edge works but I can't do right or middle button functions or 2 finger scrolling. Does anyone know why?

Simon.

---

### Post by TwinkE on 2007-07-19
Make a copy of your xorg.conf as a backup and delete the sections with the driver of wacom.  Also change your Option "device" to  "/dev/input/wacom" from "/dev/psaux"

> **troseph said:**
> Yes. I actually rebooted the machine, and still jerky movement, no corner buttons, nothing works with the exception of the two finger scrolling. Is there something I might have missed? I'm starting to find the keyboard and touchpad to me very annoying in Ubuntu. 

Here is my xorg.conf maybe I missed something, but i almost doubt it.

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "LeftEdge" "150"
Option "RightEdge" "1070"
Option "TopEdge" "100"
Option "BottomEdge" "310"
Option "FingerLow" "25"
Option "FingerHigh" "30"
Option "MaxTapTime" "180"
Option "MaxTapMove" "220"
Option "MaxDoubleTapTime" "180"
Option "HorizEdgeScroll" "0"
Option "VertEdgeScroll" "0"
Option "TapButton1" "0"
Option "TapButton2" "0"
Option "TapButton3" "0"
Option "LockedDrags" "off"
Option "VertScrollDelta" "20"
Option "HorizScrollDelta" "50"
Option "VertTwoFingerScroll" "1"
Option "HorizTwoFingerScroll" "1"
Option "MinSpeed" "1.10"
Option "MaxSpeed" "1.30"
Option "AccelFactor" "0.08"
Option "Emulate3Buttons" "true"
Option "SHMConfig" "on"
# corner buttons
Option "RTCornerButton" "0"
Option "RBCornerButton" "2"
Option "LTCornerButton" "0"
Option "LBCornerButton" "3"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by benanzo on 2007-07-20
The touchpad for the MacBooks use the device **/dev/psaux**.  You can leave it out of your config if you wish, but changing it to something other than that will likely result in a total loss of functionality.


**Troseph:**

What kind of functionality isn't working?  I noticed that you possibly have a misconfiguration in your xorg.conf file specifically referring to 1, 2 or 3 finger tapping to left/right/middle click (if that's what you wanted.)

You have 1/2/3 finger tapping disabled:
```

Option "TapButton1" "0"
Option "TapButton2" "0"
Option "TapButton3" "0"

```
Change it so that 1/2/3 finger tapping is enabled:
```

Option "TapButton1" "1"
Option "TapButton2" "3"
Option "TapButton3" "2"

```
This uses 1 finger tap to left-click, 2 finger tap to right-click and 3 finger tap to middle-click.

Some people having trouble might consider adding **Load "synaptics"** to **Section Module** to see if that helps the problem at all (no guarantee though.)

---

### Post by troseph on 2007-07-21
That did help with the two and three finger clicking, however motion is still very jerky and comes to a halt sometime when I am loading a program or something is running in the backgroud. Is that normal or might I just have a faulty touch pad?

Also, I am still having the two finger scrolling take me back a page in the history in firefox when I reach the bottom of the page. I am using Firefox version 2.0.0.5

---

### Post by thonuz on 2007-07-22
I'm on intel macbook and using Gutsy and have no problems using my touchpad and have done nothing. Then again I'm not a mac user. Right click tapping, side scrolling all works great, I'm not sure wht else there is I need, but in osx there was not right click 3 finger tapping. There is the button combo but it seems awkward and too difficult for me. My only problem has been jerkiness due to me hitting the touchpad accidentally with my finger. I don't understand why macbooks have this big button. Its like made for an animal hoof.

---

### Post by neatokino on 2007-07-22
I'm having the same problems as the others with all this.  Am running Feisty on a 1st generation Macbook Pro and have edited the /etc/X11/xorg.conf file, trying all the alternatives.  Can't invoke right click in any way shape or form, except F12.

BUT, I decided to try kubuntu, and I installed the KDE desktop just for fun.... and... lo and behold... it works in kubuntu.  Does anyone have any idea what it might be in Gnome that is keeping these xorg settings from being applied?

UPDATE, PROBLEM SOLVED:  I removed the 'touchpad' application, and the new commands started to work.  So, it may be that the GUI synaptics 'touchpad' program overrides changes inthe xorg.comf file.

TIA

---

### Post by troseph on 2007-07-23
> **neatokino said:**
> 

UPDATE, PROBLEM SOLVED:  I removed the 'touchpad' application, and the new commands started to work.  So, it may be that the GUI synaptics 'touchpad' program overrides changes inthe xorg.comf file.

I was almost suspicious of that. How did you remove it?

---

### Post by neatokino on 2007-07-23
I just went to applications--> add/remove and unchecked it.

---

### Post by neatokino on 2007-07-24
While we're on the subject of synaptics....  I'm curious if there's any way to fully emulate the behavior of the Mac trackpad, and if not, why not?   

I enjoy running Linux on my macbook pro, but, at the end of the day there are three things that make the experience not really worth it compared to the mac;  the first two are temperature control and battery life, both of which are FAR better with OSX (but rumored to be fixed or improved in Gutsy), and the third is the trackpad, which even after synaptics and syndaemon works pretty miserably in comparison to OSX.

What are the chances of someone figuring out how to make the Macbook/Mackbook Pro trackpads work exactly the same way in Linux as in OSX?  Is it a proprietary driver issue?  If trackpad, battery and temperature control were better, I'd switch OS's full time right now.  

As it stands, I'm basically just playing with Ubuntu to learn about the operating system. It's not ready yet to replace OSX on the Macbook Pro for me.

Is there hope in sight?

---

### Post by mccrackin on 2007-07-25
I agree....I have switched over to Ubuntu in full, but each time I go back into OSX for some reason I say "damn, why can't the mouse be this smooth in linux?" to myself.  Let me know if you have any fixes come your way.  Oh...the sound isn't exactly ideal either....doesn't seem to get loud enough....otherwise I'm totally content.

---

### Post by ivesjd on 2007-07-26
Neatokino, mccrakin,
Most of what you guys want trackpad wise is just in how you set it up. There are many many options and it all comes down to preference. One thing that I know does not work with the synaptics driver is "two finger on touch pad and click" for right click. But other then that it seems to work. I actually like almost everything about the mouse better. Two finger scroll is not quite as nice.

As far as battery life goes, disabling bluetooth goes a long way in helping. At least it did for me. I would say somewhere between 30-45 mins more battery life! 
I have noticed what you said about sound before. And I realized that there was a setting somewhere that was turned down a little bit. I just turned that up (I think it was something controling the highs in the sound) and It all just sounded a lot louder. Hope that is of some help for you guys.

---

### Post by neatokino on 2007-07-26
ivesjd--

I know that on some level this must come down to settings (after all, it's the same trackpad in OSX and Linux), but I haven't yet been able to come close to making the trackpad work as well in Linux as in OSX.  I have played with many different settings, including the ones posted in this thread, but the feel of the trackpad is still quite different and definitely inferior to the feel I get when using OSX.

I did, by the way, end up with these settings, which are pretty good.  I've got two-finger tapping for a right click and have disabled two-finger scrolling in favor of edge scrolling, which I quite like.  These settings, combined with a startup command of syndaemon -d -t -i 1.5  make the trackpad usable on my Macbook Pro, but still far from perfect:

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver		"synaptics" 
	Option		"SendCoreEvents"	"true" 
	Option		"Device"	"/dev/psaux" 
	Option		"Protocol"	"auto-dev" 
        Option "LeftEdge" "20"
        Option "RightEdge" "1000"
        Option "TopEdge" "17"
        Option "BottomEdge" "700"
        Option "FingerLow" "5"
        Option "FingerHigh" "7"
        Option "MaxTapTime" "180"
        Option "MaxTapMove" "220"
        Option "MaxDoubleTapTime" "180"
        Option "TapButton2" "3"
        Option "TapButton3" "2"
        Option "VertScrollDelta" "7"
        # turn off horizontal scrolling
        #Option "HorizScrollDelta" "0"
        Option "MinSpeed" "0.79"
        Option "MaxSpeed" "0.88"
        Option "AccelFactor" "0.0015"
        Option "LeftRightRepeat" "0"
        Option "UpDownRepeat" "0"
        Option "UpDownScrolling" "on"
        # turn off corner buttons
        Option "RTCornerButton" "0"
        Option "RBCornerButton" "0"
        Option "LTCornerButton" "0"
        Option "LBCornerButton" "0"
        # edge motion
        Option "EdgeMotionUseAlways" "0"
        Option "EdgeMotionMinZ" "25"
        Option "EdgeMotionMaxZ" "60"
        Option "EdgeMotionMinSpeed" "150"
        Option "EdgeMotionMaxSpeed" "200"
        Option "SHMConfig" "on"
EndSection

I borrowed most of the settings from this page:

[http://www.mikesplanet.net/ubuntu-704-on-a-macbook-pro/](http://www.mikesplanet.net/ubuntu-704-on-a-macbook-pro/)

I still have issues with the mouse flying all over the place on the screen while I type, and the touchpad is very very sensitive sometimes.  By the way, am I crazy for thinking that the sensitivity of the touchpad seems to change?  Could it be temperature dependent?  I've never noticed that on OSX.

---

### Post by cyberdork33 on 2007-07-26
> **neatokino said:**
>  I still have issues with the mouse flying all over the place on the screen while I type, and the touchpad is very very sensitive sometimes.  By the way, am I crazy for thinking that the sensitivity of the touchpad seems to change?  Could it be temperature dependent?  I've never noticed that on OSX.

There are still a lot of issues with touchpads that are addressed in the later mactel patches. In other words, they are still working on getting everything ironed out.

---

### Post by mnewsom on 2007-07-27
I've been around and around with this with no success. gsynaptics keeps telling me to set "SHMConfig" to true in xorg.conf but I'm looking at my xorg.conf and its right there, plain as day. any help would be appreciated.
I'm on a triple-booting core duo macbook running feisty.
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	Load	"synaptics"
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
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier "Synaptics Touchpad"
	Driver "synaptics"
          Option "SendCoreEvents"          "True"
          Option "Protocol"                "auto-dev"
          Option "Device"                  "/dev/psaux"
          Option "SHMConfig"               "True"
          Option "LeftEdge"      	   "100"
	  Option "RightEdge"     	   "1100"
	  Option "TopEdge"       	   "50"
	  Option "BottomEdge"    	   "300"
	  Option "FingerLow"     	   "30"
	  Option "FingerHigh"    	   "40"
	  Option "MaxTapMove"              "100"
	  Option "TapButton1"    	   "1"
	  Option "TapButton2"    	   "3"
	  Option "TapButton3"    	   "2"
	  Option "MinSpeed"      	   "0.15"
	  Option "MaxSpeed"      	   "0.90"
	  Option "AccelFactor"   	   "0.10"
	  Option "VertScrollDelta"         "25"
	  Option "HorizScrollDelta"        "30"
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
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by cyberdork33 on 2007-07-27
did you restart xorg after making the changes?

---

### Post by mnewsom on 2007-07-27
Many times. its ctrl-alt-delete, right?

---

### Post by cyberdork33 on 2007-07-27
Well on most PCs it is CTRL+ALT+BKSP, but yes that will kill xorg and restart it. Delete is a different key...

IDK why it is not working... maybe try wiping out the wacom stuff (unless you actually have one).

---

### Post by mnewsom on 2007-07-27
I commented out all the wacom stuff and no change. I suppose I should mention the (embarassing) fact that recently I told synaptic to uninstall all packages that contained the phrase "kde" in either the title or the description. Looking back I have no idea why I thought that would help. But it did teach me an important lesson about backing up xorg.conf. After restoring from the backup I've got the GUI running fine but there have been some issues. For instance, I just figured out how to return the Add/Remove... option to the application menu. So there may be any number of goofy problems on my system that would interfere with gsynaptic.
Can anybody think of any dependencies or missing packages that could prevent me from running gsynaptic?

edit - I found this at the very end end of /var/log/Xorg.0.log

Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"

It sounds relevant but I don't know what to do about it.

---

### Post by basd on 2007-08-24
Try "on" instead of "true".  That's what I am using.  See this article:

[http://ubuntu-tutorials.com/2006/12/10/tweaking-your-synaptics-touchpad-laptops-ubuntu-6061-610/](http://ubuntu-tutorials.com/2006/12/10/tweaking-your-synaptics-touchpad-laptops-ubuntu-6061-610/)

---

### Post by Gen2ly on 2007-08-29
I make sure to add

```
Option "TapButton1" "0"
```

because touchpad tapping is far to sensitive.

---

### Post by phonky on 2007-09-10
Hi Guys

Mi Touchpad is almost working fine for me. But I have a weird effect which someone (troseph?) described further up and didn't get any help on this.

In fact, when I do two-finger scrolling in firefox, the browser goes back (and forth) to the last (next) page.

Is this possibly a firefox issue or can I tweak something in the xorg.conf?

xorg.conf section:

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"Device"	"/dev/psaux"
	Option		"SendCoreEvents"	"True"
	Option		"SHMConfig"		"True"
	Option		"Protocol"	"auto-dev"
	Option		"LeftEdge"	"100"
	Option		"RightEdge"	"1100"
	Option		"TopEdge"	"50"
	Option		"BottomEdge"	"300"
	Option 		"MaxTapTime" "180"
	Option 		"MaxTapMove" "220"
	Option 		"MaxDoubleTapTime" "180"
	Option 		"VertScrollDelta" "25"
	Option		"HorizScrollDelta" "30"
	Option 		"VertTwoFingerScroll" "true"
	Option		"HorizTwoFingerScroll" "true"
	Option		"FastTaps"	"true"
	Option 		"TapButton2" "3"
	Option 		"TapButton3" "2"
	Option		"MinSpeed"		"1.10"
	Option		"MaxSpeed"		"2.10"
	Option		"AccelFactor"		"0.35"
	Option		"Emulate3Buttons"	"true"
	Option		"RTCornerButton"	"0"
	Option		"RBCornerButton"	"3"
	Option		"LTCornerButton"	"0"
	Option		"LBCornerButton"	"2"
EndSection

thanks for any help

---

### Post by cyberdork33 on 2007-09-10
It is a config in firefox I am sure. It sounds like it is interpreting it as the side buttons that are on some mice, and thus uses the default actions associated with these... Back/Forward.

---

### Post by dmber on 2007-09-12
> **phonky said:**
> Hi Guys

Mi Touchpad is almost working fine for me. But I have a weird effect which someone (troseph?) described further up and didn't get any help on this.

In fact, when I do two-finger scrolling in firefox, the browser goes back (and forth) to the last (next) page.

Is this possibly a firefox issue or can I tweak something in the xorg.conf?



with two finger scrolling enabled, you will probably want to change firefox's horizontal scrolling behavior.  to do so, open firefox, go to the URL "about:config", and change the following settings:

mousewheel.horizscroll.withnokey.action from 2 to - 0
mousewheel.horizscroll.withnokey.numlines from -1 to 1

from:
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

---

### Post by dmber on 2007-09-12
can i set the top left and top right corners to run F-keys?  i'd like to hit the top left to show the desktop with compiz and the top right to show all applications.

thanks.

---

### Post by phonky on 2007-09-13
Thank you dmber,

I just wanted to post the solution, which I found
here:

[http://apple.slashdot.org/article.pl?sid=05/02/11/173236](http://apple.slashdot.org/article.pl?sid=05/02/11/173236)

but you were faster.

Thank you very much
fabio

---

### Post by MarkieB on 2007-09-30
> **dmber said:**
> can i set the top left and top right corners to run F-keys?  i'd like to hit the top left to show the desktop with compiz and the top right to show all applications.
thanks.

My question is similar; as well as the touchpad, there are actual mouse buttons on my notebook; in windows, I would map the left mouse button to alt-F4; is it possible to map that in ubuntu?

One other mapping I made, was from the lower-left corner tap zone to the 'start' button; is it possible to map a corner tap zone to open a specific menu in ubuntu?

cheers

Mark

---

### Post by zmjjmz on 2007-10-02
I had the same troubles as Troseph and Phonky, but in Opera...
I don't know how to change the settings there...

---

### Post by Smutronic on 2007-12-06
Hey guys,
i am still recieving the error message when i try to start gsynaptics:
"GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics".

My xorg.file:
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
        Option 		"SHMConfig"		"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
        Option 		"SHMConfig"		"true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"	"SendCoreEvents"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

```

Is it possible that i don´t have the synaptics driver?

---

### Post by StephUb on 2007-12-07
I try:
using gsynaptics / qsynaptics / xorg.conf
No success, i can stop the touchpad, but cannot get the two/three fingers to work

any tips?

Gutsy on a laptop sony VIAO FS790B
i did follow all the how to...

thanks

---

### Post by henriquemaia on 2007-12-10
> **Smutronic said:**
> Hey guys,
i am still recieving the error message when i try to start gsynaptics:
"GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics".

My xorg.file:
```

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
        Option         "SHMConfig"        "true"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
        Option         "SHMConfig"        "true"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"    "SendCoreEvents"

# Uncomment if you have a wacom tablet
#    InputDevice     "stylus"    "SendCoreEvents"
#    InputDevice     "cursor"    "SendCoreEvents"
#    InputDevice     "eraser"    "SendCoreEvents"
EndSection

```Is it possible that i don´t have the synaptics driver?


I have the same issue and this looks like a limitation from the xorg server shipped with gutsy. Previous versions had this working.

---

### Post by DJBaz on 2007-12-11
thanks for this awesome thread :) im attempting to be linux only (apart from when I use Pro Tools in os x) and this thread has sorted my trackpad woes!

Thanks again!!!

---

### Post by khiraly on 2008-01-02
Hi!

Maybe somebody can help me:
Is it possible to use multi finger scrolling on a regular notebook (hp-compaq nx9105), or this multi finger scrolling and two finger click is a hardware feature and it is exlusive on the macintosh hardware?

Do I need buy a macbook if I want to use multi finger scrolling, even if i have linux and synaptics driver (0.14.6, as in ubuntu gutsy) ?

Hope somebody can help me.

I have tried out this settings: [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

But dont work on my laptop.

Any hint?

---

### Post by cyberdork33 on 2008-01-03
I believe that there are hardware limitations but they are not Mac specific.

---

### Post by mabovo on 2008-01-19
Hy, 

I have a MacBook 2nd generation running Hardy Heron with xserver-xorg 7.3.

Bellow is an example of xorg.conf which I don't know if there is any options in conflicting with touchpad. I am just starting to test it and see if it works better than without xorg.conf.

I know that Hardy don't need a xorg.conf file but I would like to know if it is still necessary in order to configure synaptics ?

```

# xorg.conf (X.Org X Window System server configuration file)
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
	Load	"synaptics"
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
	Identifier "Synaptics Touchpad"
	Driver "synaptics"
          Option "SendCoreEvents"          "True"
          Option "Protocol"                "auto-dev"
          Option "Device"                  "/dev/psaux"
          Option "SHMConfig"               "True"
#	  Option "SHMConfig"		   "on"
#	  Option "GuestMouseOff"   	   "True"     # disables external mice
	  Option "GuestMouseOff"	   "False"    # enables external mice
          Option "LeftEdge"      	   "100"
#	  Option "LeftEdge" 		   "150"
	  Option "RightEdge"     	   "1100"
#	  Option "RightEdge"		   "1070"
	  Option "TopEdge"       	   "50"
#	  Option "TopEdge"		   "100"
	  Option "BottomEdge"    	   "300"
#	  Option "BottomEdge"		   "310"
	  Option "FingerLow"     	   "30"
#	  Option "FingerLow"		   "25"
#	  Option "FingerLow"		   "20"
	  Option "FingerHigh"    	   "40"
#	  Option "FingerHigh"		   "30"
#	  Option "MaxTapTime"		   "180"
	  Option "MaxTapTime"		   "150"
#	  Option "MaxTapMove"              "90"
	  Option "MaxTapMove"              "100"
#	  Option "MaxTapMove"		   "220"
#	  Option "MaxDoubleTapTime"	   "180"
	  Option "TapButton1"    	   "1"
	  Option "TapButton2"    	   "3"
	  Option "TapButton3"    	   "2"
	  Option "LockedDrags"		   "off"
	  Option "MinSpeed"      	   "0.15"
#	  Option "MinSpeed"		   "0.5"
#	  Option "MinSpeed"		   "1.10"
#	  Option "MaxSpeed"      	   "0.90"
#	  Option "MaxSpeed"		   "1.30"
	  Option "MaxSpeed"		   "2.10"
#	  Option "MaxSpeed"		   "3.5"
#	  Option "AccelFactor"		   "0.08"
	  Option "AccelFactor"   	   "0.10"
#	  Option "AccelFactor"		   "0.35"
	  Option "VertScrollDelta"         "25"
#	  Option "VertScrollDelta"	   "20"
	  Option "HorizScrollDelta"        "30"
#	  Option "HorizScrollDelta"	   "50"
#	  Option "HorizEdgeScroll"	   "0"
#	  Option "VertEdgeScroll"	   "0"
#	  Option "Emulate3Buttons"	   "true"
# corner buttons
#	  Option "RTCornerButton"	   "0"
#	  Option "RBCornerButton"	   "2"
#	  Option "RBCornerButton"	   "3"
#	  Option "LTCornerButton"	   "0"
#	  Option "LBCornerButton"	   "3"
#	  Option "LBCornerButton"	   "2"
# two finger scrolling
#	  Option "VertTwoFingerScroll"	   "1"
	  Option "VertTwoFingerScroll"	   "true"
#	  Option "HorizTwoFingerScroll"	   "1"
	  Option "HorizTwoFingerScroll"	   "true"
	  Option "FastTaps"		   "true"
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
#	Identifier	"Configured Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
#	Monitor		"Configured Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Thanks for any help.

---

### Post by mabovo on 2008-01-19
I made some changes in xorg.conf but it is not recognized in Hardy ?

```

# xorg.conf (X.Org X Window System server configuration file)
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

Section "Module"
	Load	"synaptics"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "InputDevice"
	Identifier "Synaptics Touchpad"
	Driver "synaptics"
          Option "SendCoreEvents"          "True"
          Option "Protocol"                "auto-dev"
          Option "Device"                  "/dev/psaux"
          Option "SHMConfig"               "True"
#	  Option "SHMConfig"		   "on"
#	  Option "GuestMouseOff"   	   "True"     # disables external mice
	  Option "GuestMouseOff"	   "False"    # enables external mice
          Option "LeftEdge"      	   "100"
#	  Option "LeftEdge" 		   "150"
	  Option "RightEdge"     	   "1100"
#	  Option "RightEdge"		   "1070"
	  Option "TopEdge"       	   "50"
#	  Option "TopEdge"		   "100"
	  Option "BottomEdge"    	   "300"
#	  Option "BottomEdge"		   "310"
	  Option "FingerLow"     	   "30"
#	  Option "FingerLow"		   "25"
#	  Option "FingerLow"		   "20"
	  Option "FingerHigh"    	   "40"
#	  Option "FingerHigh"		   "30"
#	  Option "MaxTapTime"		   "180"
	  Option "MaxTapTime"		   "150"
#	  Option "MaxTapMove"              "90"
	  Option "MaxTapMove"              "100"
#	  Option "MaxTapMove"		   "220"
#	  Option "MaxDoubleTapTime"	   "180"
	  Option "TapButton1"    	   "1"
	  Option "TapButton2"    	   "3"
	  Option "TapButton3"    	   "2"
	  Option "LockedDrags"		   "off"
	  Option "MinSpeed"      	   "0.15"
#	  Option "MinSpeed"		   "0.5"
#	  Option "MinSpeed"		   "1.10"
#	  Option "MaxSpeed"      	   "0.90"
#	  Option "MaxSpeed"		   "1.30"
	  Option "MaxSpeed"		   "2.10"
#	  Option "MaxSpeed"		   "3.5"
#	  Option "AccelFactor"		   "0.08"
	  Option "AccelFactor"   	   "0.10"
#	  Option "AccelFactor"		   "0.35"
	  Option "VertScrollDelta"         "25"
#	  Option "VertScrollDelta"	   "20"
	  Option "HorizScrollDelta"        "30"
#	  Option "HorizScrollDelta"	   "50"
#	  Option "HorizEdgeScroll"	   "0"
#	  Option "VertEdgeScroll"	   "0"
# using corner buttons
# 1=Left Button
# 2=Middle Button
# 3=Right Button
#	  Option "Emulate3Buttons"	   "true"
#	  Option "RTCornerButton"	   "0"
#	  Option "RBCornerButton"	   "2"
#	  Option "RBCornerButton"	   "3"
#	  Option "LTCornerButton"	   "0"
#	  Option "LBCornerButton"	   "3"
#	  Option "LBCornerButton"	   "2"
# using two finger scrolling like OSX
#	  Option "VertTwoFingerScroll"	   "1"
	  Option "VertTwoFingerScroll"	   "true"
#	  Option "HorizTwoFingerScroll"	   "1"
	  Option "HorizTwoFingerScroll"	   "true"
	  Option "FastTaps"		   "true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
EndSection

Section "ServerLayout"
	Identifier	    "Default Layout"
        Screen              "Default Screen"
	InputDevice         "Generic Keyboard"
	InputDevice	    "Configured Mouse"
        Inputdevice         "Synaptics Touchpad"
EndSection

```

---

### Post by SoliDphantoM on 2008-01-21
> **khiraly said:**
> Hi!

Maybe somebody can help me:
Is it possible to use multi finger scrolling on a regular notebook (hp-compaq nx9105), or this multi finger scrolling and two finger click is a hardware feature and it is exlusive on the macintosh hardware?

Do I need buy a macbook if I want to use multi finger scrolling, even if i have linux and synaptics driver (0.14.6, as in ubuntu gutsy) ?

Hope somebody can help me.

I have tried out this settings: [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

But dont work on my laptop.

Any hint?

I can confirm you don't need a mac to get this to work.  I have a Dell Inspiron 700m and have gotten the two finger click to work, however, I have not been successful with the two finger scrolling. The scroll wheel scrolling will also work but these are the only options I've tested.

I had a friend try it on his HP and he's gotten the two finger click to work as well.  \\:D/ 

Like the OP says, I think you just need a synaptics touchpad for this to work. Not sure of the limitations on this, but my friend said he's had his HP for 5 years. So if you computer's not that old you should be good!

---

### Post by mabovo on 2008-01-22
Finally I get touchpad synaptics working together with xorg.conf on Hardy Heron.
The only problem I have found is the incompatibility with Compiz so disabling desktop effects was the solution because some plugins in Compiz screw up with the synaptics behavior in X.
Now I need to learn how to configure some options to better make usable my touhpad.
Thanks for this tutorial, it was very helpfull.

---

### Post by mabovo on 2008-01-27
I would appreciate very much if somebody posted here a tip on how to get "drag" and "drop" working in synaptics ?

I realized today that pressing bottom pad while swapping touchpad I can get the mouse drag and drop movement. Thanks anyway !

---

### Post by njpatel on 2008-02-02
Hi,

I was wondering if there was an option to turn off the synaptics touchpad when an external mouse is connected? I normally use an external mouse, and always manage to hit the pad when typing (which normally ends up focusing another window).

Thanks in advance,

Neil

---

### Post by RebounD11 on 2008-02-02
there is a rather crude way... comment out the part about synaptics touchpad in the xorg.conf and leave only the part with your external mouse...

However you will have to uncomment it when you want to use it again.

---

### Post by erfahren on 2008-02-02
> **njpatel said:**
> Hi,

I was wondering if there was an option to turn off the synaptics touchpad when an external mouse is connected? I normally use an external mouse, and always manage to hit the pad when typing (which normally ends up focusing another window).

Thanks in advance,

Neil
if you don't have that option in your regular mouse settings (it seems that some have touchpad options and some don't - I have no idea why!)

anyway, there's two programs that you can try for additional configuration (and probably to disable it).
I'll just give you the names of both and let you look at the descriptions to decide which you want to try first.

first you need to add a line to xorg.conf to use them - so do this:
open a terminal - Applications > Accessories > Terminal - and back up your current xorg.conf
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_back

```
then open it in the text editor to edit (if using Kubuntu use "kate" , if Xubuntu use "mousepad" - instead of "gedit")
```

gksudo gedit /etc/X11/xorg.conf

```
scroll down to the Synaptic section - it will look something like:
```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"MaxTapTime"		"0"
        **Option          "SHMConfig"             "on"**
EndSection

```
copy and paste that line I have in bold into that section (what it does is enables the use of shared memory for additional configuration settings for the touchpad if needed) - and save the file


now do this: open up Synaptic Package Manager (no relation - lol ) - System > Administration > Synaptic Package Manager - and search for the packages:
**GSynaptics and QSynaptics** - you might want to try QSynaptics first - but it's up to you

good luck!

---

### Post by hardawayd on 2008-02-02
On my Macbook Pro the xorg.conf file does not have any reference to a trackpad in it but the trackpad works. Using Hardy--latest version.  Anyone know whats up with that?

---

### Post by cyberdork33 on 2008-02-03
> **hardawayd said:**
> On my Macbook Pro the xorg.conf file does not have any reference to a trackpad in it but the trackpad works. Using Hardy--latest version.  Anyone know whats up with that?You can add it. Hardy has a very minimal xorg.conf file because it really isn't needed on the new version of xorg.

you can try this script that turns your touchpad off when you connect a mouse:
[http://linuxtidbits.wordpress.com/2007/09/07/little-script-to-toggle-touchpad/](http://linuxtidbits.wordpress.com/2007/09/07/little-script-to-toggle-touchpad/)

---

### Post by pjfitzgibbons on 2008-02-04
Here are the changes required for my Lenovo T60 and Hardy Alpha 4 on a fresh install (Important that this was a fresh install)

Touchpad had minimal operation, no drag-drop, no scrolling.  xserver-xorg-input-synaptics was installed automatically by HAL detection.

xorg.conf changes:

Add before the current Sections :
```

Section "Module"
        Load "synaptics"
EndSection

```

Add the following after the current "Section "InputDevice" ... "Configured Mouse" :
```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents" "true"
        Option          "Device" "/dev/psaux"
        Option          "Protocol" "auto-dev"
        Option          "HorizScrollDelta" "0"
        Option          "SHMConfig" "true"
EndSection

```

Add at the end :
```

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

```

Restart X (ctl-alt-backspace)

Explanation:
Yes, the new X.org 7.3 has minimized the xorg.conf contents.  (Unfortunately), the input hooks are not minimized, so restoring the proper Synaptics operation requires replacing the previous "verbose" conf.  For video, the extra configuration information "appears" to be ignored (I have to wait 'till the morning to double-check my external monitor.

As far as I can tell, there is no conflict with Compiz.   Also, drag-drop and window-movement was restored after this change.



I installed gsynaptic for the configuration GUI via System -> Preferences -> Touchpad.   My favorite trick is the iPod-style circular scrolling.

Hope this helps y'all.

Peter Fitzgibbons

---

### Post by cyberdork33 on 2008-02-05
> **pjfitzgibbons said:**
> Yes, the new X.org 7.3 has minimized the xorg.conf contents.  (Unfortunately), the input hooks are not minimized, so restoring the proper Synaptics operation requires replacing the previous "verbose" conf.  For video, the extra configuration information "appears" to be ignored (I have to wait 'till the morning to double-check my external monitor.Yes, at least a lot of the sections (monitor capabilities and such is all detected on the fly). You can still set the driver and a few other options from the xorg.conf.

---

### Post by njpatel on 2008-02-07
> **erfahren said:**
> if you don't have that option in your regular mouse settings (it seems that some have touchpad options and some don't - I have no idea why!)

anyway, there's two programs that you can try for additional configuration (and probably to disable it).
I'll just give you the names of both and let you look at the descriptions to decide which you want to try first.

...

good luck!


Thanks for this, I'll try it out when I get home.

--Neil

---

### Post by benplaut on 2008-03-22
bump, and a really weird question.  First, this works great.  Almost as good (in software) as a macbook, and even better with the awesome touchpad surface on a thinkpad.

At first, i thought it was acting sporadically... i would lift my fingers when i ran out of room and bring them back to the other side of the pad to continue scrolling.  It would scroll up with me.  Turns out, the pad was picking up my movements a few mm above the pad surface :lolflag:

Any suggestions?  It's probably some sort of sensitivity problem, but i'm not sure which.

while i'm at it, is there any way to make the touchpad "2 finger scroll only," removing the regular pointer function?

---

### Post by cyberdork33 on 2008-03-22
you need to turn the sensitivity for detecting a touch down a bit. see 'man synaptics' for details on the available options.

---

### Post by Digitz on 2008-05-17
Hi i have a Macbook Core2Duo with 8.04 installed on it and my trackpad isn't working like it should.

When i place my finger somewhere on the trackpad, the pointer on the screen directly goes to a position on the screen (example: when i place my finger on the upper-left corner of the trackpad, my mousepointer immediately goes to the left-center of the screen, when i touch the upper-right corner it goes to the right-center etc etc). This makes it impossible to navigate via the trackpad...

I've searched like hell and tried different settings in xorg.conf, but nothing worked so far. Was hoping someone can help me :)

**sigh...fixed...a reboot worked...im gonna hit myself!*

---

### Post by attenpeter on 2008-05-30
Hi,

if I try to configure my touchpad behaviour I always notice the following no matter what I change: The cursor in mac os smoothly moves in a straigt line from one edge to the other if I drag my finger diagonally... In ubuntu, the cursor first moves up, then down, like small steps...

Pictures: ;)

mac os curosr movement:
```

\
 \
  \
```

ubuntu cursor movement:
```

|
 -
  |
   -
```

I don't know if this is a driver or configuration issue... Any ideas how to fix this? (I use the configuration from this link: [https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-b746291600b14e15576a94b5a5ae7d325138b8cb](https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-b746291600b14e15576a94b5a5ae7d325138b8cb) )

EDIT: oh yes, I have a macbook3,1 (santa rosa c2d) if it matters

cu,
peter

---

### Post by cyberdork33 on 2008-05-30
a few people have complained about this, but nobody has found the issue yet as far as I know. You should search/post in the new Apple Users forum though, this one is just an archive.

[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

### Post by k3y5rmy1if3 on 2008-06-01
Nope, no worky. I followed the tutorial, saved the xorg.config (with all my options) , logged out of X, and it's exactly the same...how depressing.

heres my inputdevice section if it helps...oh yeah, and i'm on 7.10 i beleive...


```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option "SendCoreEvents"          "True"
        Option "Protocol"                "auto-dev"
        Option "Device"                  "/dev/psaux"
        Option "SHMConfig"               "True"
        Option "LeftEdge" "150"
        Option "RightEdge" "1070"
        Option "TopEdge" "100"
        Option "BottomEdge" "310"
        Option "FingerLow" "25"
        Option "FingerHigh" "30"
        Option "MaxTapTime" "180"
        Option "MaxTapMove" "220"
        Option "MaxDoubleTapTime" "180"
        Option "HorizEdgeScroll" "0"
        Option "VertEdgeScroll" "0"
        Option "TapButton1" "0"
        Option "TapButton2" "0"
        Option "TapButton3" "0"
        Option "LockedDrags" "off"
        Option "VertScrollDelta" "20"
        Option "HorizScrollDelta" "50"
        Option "VertTwoFingerScroll" "1"
        Option "HorizTwoFingerScroll" "1" 
        Option "MinSpeed" "1.10"
        Option "MaxSpeed" "1.30"
        Option "AccelFactor" "0.08"
        Option "Emulate3Buttons" "true"
        Option "SHMConfig" "on"
        # corner buttons
        Option "RTCornerButton" "0" 
        Option "RBCornerButton" "2"
        Option "LTCornerButton" "0"
        Option "LBCornerButton" "3"
EndSection 

```

---

### Post by unregisteredUser on 2008-06-09
anyone know how to disable tap and drag?

---

### Post by erfahren on 2008-06-09
> **unregisteredUser said:**
> anyone know how to disable tap and drag?I looked through the [man page](http://linux.die.net/man/5/synaptics) and it doesn't look like you can disable just dragging after a tap. 

there is the LockedDrags option though - take a look at that

if you're having problems with inadvertantly dragging things you could try messing around with the regular mouse settings (drag threshold) until you find a setting you can live with.

---

### Post by flaggh on 2008-06-21
Using these instructions, when I first setup my trackpad, I was able to quickly triple finger tap twice and it would be like I was holding down the middle mouse button.  This behavior disappeared a while back after updating and now I'm anxious to get it to work again.  Anybody know why this disappeared or how I can get it to work again?

---

