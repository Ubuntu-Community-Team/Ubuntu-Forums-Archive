---
title: "Intermittent system freezes since upgrade..."
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2006-08-10
I upgraded to dapper a few weeks ago, and managed to muddle my way through the bcom wireless issue I developed. However, now my system will occaisionally freeze. I don't seem to be able to do anything but a power-off reboot. Maybe I'm missing something? absolutely nothing responds when this happens.

---

### Post by nalmeth on 2006-08-10
What kind of video card do you have? Have you installed any drivers for it?

How much RAM do you have?

---

### Post by Papa-san on 2006-08-10
How to check for video card?
256 megs of ram

---

### Post by Ptero-4 on 2006-08-10
use this command on the terminal
```
sudo lspci
```

Use your password when it asks for a password.

---

### Post by Papa-san on 2006-08-10
Thanks...I forgot!
```
 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY

```

I had the drivers installed before the upgrade, and when prompted in regards to whether I wanted to keep the old settings or change to new, I left them the same.I don't know if video drivers were left or not...

---

### Post by nalmeth on 2006-08-10
OK, you may want to try reinstalling the drivers. Do you know how to do this?

---

### Post by Papa-san on 2006-08-11
OK...
I do not... Heck ndiswrapper was bad enough! lol

---

### Post by Papa-san on 2006-08-12
Hi,
I do not know how to install the drivers. I posted on an old thread that relates, but there were no solutions shown that I could understand...

(I'm really not all that sharp!) 

Once I get this figured out, I prolly won't upgrade next time... Just stick with what works...

---

### Post by Papa-san on 2006-08-12
OK...someone ended up doing an xorg.conf.txt file for my particular laptop... I have the text copied, but do not know what to do with it from here. I'm assuming it would be a gedit thing, but where do I locate the appropriate file to edit, and what do I need to look out for?

Please try to be patient with me... I'm trying to get the hang of this linux thing!

---

### Post by Papa-san on 2006-08-13
OK...since it seems I have been dropped like a hot rock, here's my plan:

(If someone thinks it's a bad idea, please let me know.)

I cannot seem to keep this thing from freezing long enough to get through more than about four pages, so this is hopefully going to post before I crash...

I managed to search and bookmark a page that seems good... The writer has a system that is identical to mine, and has written a 'xorg.conf.txt' file. I am assuming this is what needs to be changed. 

The way I'll go about it is thus:

In terminal, I am going to 'sudo gedit xorg.conf'
(I have done this, and I get a totally blank file, so I am hoping it is the right one)

Then I am going to paste:
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen					0  "Screen0" 0 0
	InputDevice    "Mouse0"			"CorePointer"
	InputDevice    "Keyboard0"	"CoreKeyboard"
EndSection

Section "Files"
	RgbPath      "/usr/lib/X11/rgb"
	ModulePath   "/usr/lib/modules"
  FontPath     "/usr/share/fonts/misc:unscaled"
	FontPath     "/usr/share/fonts/75dpi:unscaled"
	FontPath     "/usr/share/fonts/100dpi:unscaled"
	FontPath     "/usr/share/fonts/Type1"
	FontPath     "/usr/share/fonts/TTF"
	FontPath     "/usr/share/fonts/corefonts"
	FontPath     "/usr/share/fonts/freefont"
	FontPath     "/usr/share/fonts/sharefonts"
	FontPath     "/usr/share/fonts/artwiz"
	FontPath     "/usr/share/fonts/terminus"
	FontPath     "/usr/share/fonts/ttf-bitstream-vera"
	FontPath     "/usr/share/fonts/unifont"
	FontPath     "/usr/share/fonts/default/ghostscript:unscaled"
	FontPath     "/usr/share/fonts/ukr:unscaled"
EndSection

Section "Module"
	Load  "dbe"
	Load  "GLcore"
	Load  "dri"
	Load  "glx"
	Load  "extmod"
	Load  "record"
	Load  "xtrap"
	Load  "type1"
	Load  "freetype"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option      "XkbLayout"   "us"
	Option      "XkbModel"    "dell"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "synaptics"
	Option			"Protocol"	"auto"
	Option			"Device"		"/dev/input/mouse0"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Dell"
	ModelName    "14.1 XGA LCD"
	HorizSync		 31.5-48.5
	VertRefresh  59.0-75.0
	Option       "dpms"
	DisplaySize  289 217
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "Radeon Mobility M6 LY"
	BusID       "PCI:1:0:0"
	Option      "DDCMode"      "on"
  Option      "BIOSHotkeys"  "on"
	Option      "pci retry" 
	Option      "AGPMode"      "4"
	Option      "AGPFastWrite" "on"
	Option      "BIOSHotKeys"  "on"
EndSection

Section "Screen"
	Identifier    "Screen0"
	Device        "Card0"
	DefaultDepth	24
	Monitor       "Monitor0"
	SubSection "Display"
		Viewport  0 0
		Depth     24
	EndSubSection
EndSection

``` and save it. Once I re-boot, should this resolve the issue with my video driver?

I am not sure how this all works, but I haven't found any directions or other help in fixing my crash issue... So I am willing to give it a try...

---

### Post by Papa-san on 2006-08-13
OK... since I am talking to myself... (LOL)

Evidently it is the /etc/X11/xorg.conf that I am editing. Glad I found that...
Here are the contrents of that current file:```
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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9000 (M6 LY)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 9000 (M6 LY)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection 
``` There are quite a few items in here that are different... Am I supposed to just change the applicable entries? Or do they all need to be removed and the new one copied and saved into it?

I ran the code:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```It said it was overwriting a possibly modified file and backed it up. (I never did anything to it, so it must actually have an upgrade (update?) in it)

---

### Post by Papa-san on 2006-08-15
Well, tried everything I could come up with and no luck...
Any of the times I have tried to edit /etc/X11/xorg.conf, I re-boot and come up with an xserver failure.

I am at a loss...

Any help?  Please?

The above post shows a "Radeon Mobility 9000" card, and I don't believe this is what it is. I think it is a "Radeon Mobility 7500". I might be wrong. 

I am noticing a few threads where this is an issue. I think someone in development assumed the 9000 drivers would cover the others, and it doesn't. I really wish I knew what I was doing!

---

### Post by Papa-san on 2006-08-16
I love this community!

A guy in the laptop support forum built me the solution! :
But don't despair, I've attached an xorg.conf file that should sort all of your problems out. As long as you are in Dapper 6.06! i.e Not Breezy or Warty, or Edgy.
```
:

[code]# /etc/X11/xorg.conf (xorg X Window System server configuration file)
# To update this file, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option		"NoAccel"	"false"
#	Option		"AGPMode"	"x4"
#	Option		"AGPFastWrite"	"true"
#	Option		"MonitorLayout"	"LVDS"
#	Option		"EnablePageFlip""true"
#	Option		"RenderAccel"	"true"
#	Option		"AccelMethod"	"XAA"
#	Option		"DynamicClocks" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```


So U need to:
sudo gedit /etc/X11/xorg.conf
File / Save As /
/etc/X11/xorg.conf.old
File / New
copy all from above attachment & paste into new blank tab of gedit
File / Save As /
/etc/X11/xorg.conf
Yes you want to overwrite the existing file.

Reboot & post back

---

