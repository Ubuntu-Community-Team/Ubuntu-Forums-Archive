---
title: "Spanning Desktops Vertically - a sort of how-to"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by djsroknrol on 2006-04-21
I opologize for posting this here, as I've tried to post in the how-to section and it never showed up there...I'm hoping this thread will be moved there...

There has been a lot of people with ATI  cards trying to get “Big Desktops” going. I've been playing with my Xorg.conf on and off for some time, and finally found a solution to span vertically which I want to share.

 I'm running a Radeon 9200SE, which is a dual head card. The card is connected to a 17” and a 15”, The DV-I port is secondary, so the 17” is connected to VGA port, and the 15” connected with an adapter to the DV-I port. Both monitors are CRT's. 

The difference in my layout is that my second monitor sits on top of my computer desk shelf above the first one. I figured, if  it can span side to side, why not up and down? That's what I set out to do. I wanted to keep it simple, and decided to work with the OSS Radeon driver. After some searching online,  I found out that it does support 2D and 3D acceleration and it runs it's own “pseudo-Xinerama” scheme. That's a plus as you'll see soon. 

Here is a list of cards it supports:

 R100        Radeon 7200
RV100       Radeon 7000(VE), M6
RS100       Radeon IGP320(M)
 RV200       Radeon 7500, M7, FireGL 7800
RS200       Radeon IGP330(M)/IGP340(M)
 RS250       Radeon Mobility 7000 IGP
 R200        Radeon 8500
, 9100, FireGL 8800/8700
RV250       Radeon 9000PRO/9000, M9
RS300       Radeon 9100 IGP
RS350       Radeon 9200 IGP
RS400       Radeon XPRESS 200/200M IGP
RV280       Radeon 9200PRO/9200/9200SE, M9+
R300        Radeon 9700PRO/9700/9500PRO/9500/9600TX, FireGL  X1/Z1  (2Donly)
R350        Radeon 9800PRO/9800SE/9800, FireGL X2 (2D only)
R360        Radeon 9800XT (2d only)
RV350       Radeon 9600PRO/9600SE/9600, M10/M11, FireGL T2 (2D only)
RV360       Radeon 9600XT (2d only)
RV370       Radeon X300, M22 (2d only)
RV380       Radeon X600, M24 (2d only)
RV410       Radeon X700, M26 (2d only)
R420        Radeon X800 (2d only)
R423        Radeon X800 PCIE (2d only)
R430        Radeon X800, X800 XL, M28 (2d only)
R480        Radeon X850 (2d only)

First, I started with a fresh Xorg file:
```
sudo dpkg-reconfigure xserver-xorg
```

Take the defaults. The file will leave a backup so you can always go back to your previous configuration.


Then I edited the Section “Device” lines to look like this. Replace my identifier with yours from the list above. I inserted “Radeon” in the Driver line in place of “ati”:

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9200 SE (RV280)"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option "RenderAccel" "True"
	Option "SubPixelOrder" "None"
	Option "ColorTiling" "False"
	Option "MergedFB" "True"
	Option "MetaModes" "1024x768-1024x768 1024x768-1024x768"
	Option "MergedDPI" "100 100"
	Option "CRT2Position" "Below"
EndSection

```

This is where a lot of the magic begins. MergedFB is important here. That is what runs the pseudo-Xinerama. Seeing as the monitors were close, I used the MetaModes to set the desktop the same for both monitors. CRT2Position has 4 values, “RightOf” “LeftOf” “Above” and “Below”. Note that my example says “Below”. I wanted to have windows slide down to the other monitor”Below”. Then, I enter the second monitor and identify the two monitors and both screens:

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9200 SE (RV280)secondary"
	Driver		"radeon"
	BusID		"PCI:1:0:1"
	
EndSection

Section "Monitor"
	Identifier	"DELL D1025TM"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"PRINCETON ULTRA 51"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"ATI Technologies, Inc. Radeon 9200 SE (RV280)"
	Monitor		"DELL D1025TM"
	DefaultDepth	24
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"ATI Technologies, Inc. Radeon 9200 SE (RV280)secondary"
	Monitor		"PRINCETON ULTRA 51"
	DefaultDepth	24
	
EndSection
```

Note the BusID's on both heads. I do believe if they are not ID'ed properly, at the least you'll have a cloned (exact duplicate) setup and at worst a broken X. Double check your work here. You can find  a lot of information in Applications>System Tools>System Information(Hardinfo). Then I rewrote a new “ServerLayout” section:

```
Section "ServerLayout"
	Identifier	"Dual Head Layout"
	Screen  	"Screen0" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection
```

Notice there's only mention of 1 screen (remember K.I.S.S.). The focus is on the main screen here. Save and CTRL-ALT-BACKSPACE out and log back in...It worked great for me the very first time....So good in fact, that I decided to go a little further. After the “DRI” section, I added this:

```
Section "Extensions"
	Option "Composite" "Enable"
EndSection

```

With that, I was able to keep my eye candy like 3ddesk, xcompmgr and xdesktopwaves. They all work and span both viewpoints. Here is my complete Xorg.conf for evaluation:

```
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
	Load	"i2c"
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
	Identifier	"ATI Technologies, Inc. Radeon 9200 SE (RV280)"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option "RenderAccel" "True"
	Option "SubPixelOrder" "None"
	Option "ColorTiling" "False"
	Option "MergedFB" "True"
	Option "MetaModes" "1024x768-1024x768 1024x768-1024x768"
	Option "MergedDPI" "100 100"
	Option "CRT2Position" "Below"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9200 SE (RV280)secondary"
	Driver		"radeon"
	BusID		"PCI:1:0:1"
	
EndSection

Section "Monitor"
	Identifier	"DELL D1025TM"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"PRINCETON ULTRA 51"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"ATI Technologies, Inc. Radeon 9200 SE (RV280)"
	Monitor		"DELL D1025TM"
	DefaultDepth	24
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"ATI Technologies, Inc. Radeon 9200 SE (RV280)secondary"
	Monitor		"PRINCETON ULTRA 51"
	DefaultDepth	24
	
EndSection


Section "ServerLayout"
	Identifier	"Dual Head Layout"
	Screen  	"Screen0" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

```

Very clean and simple and works great. There's a lot of useful information in man Radeon. I hope this will help make someone's dual monitor layout easier to set up.

---

