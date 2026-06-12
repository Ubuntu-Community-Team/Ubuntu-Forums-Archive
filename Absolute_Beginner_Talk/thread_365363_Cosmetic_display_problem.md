---
title: "Cosmetic display problem"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by Flufflebuns on 2007-02-19
I'm a complete Ubuntu noob, and I have a simple stupid question, but have no idea how to solve it.  My desktop background is centered and only takes up about 3/4 the screen with a border of about 3 inches of black around it.  

I imagine I have to change the resolution, but at current it's at the max resolution ( 1024x768 ).  Before I installed Ubuntu I checked max display specs through windows it's 1600x1200, but there is no option to make it that size.  It can only go two sizes smaller, and when I try those it glitches and nothing works (have to wait for it to go back to regular size without confirming).

I think I need to install new drivers for ATI Mobility Radeon M4 too, but have no idea how to do that either.  Can anyone help?  I'm not sure what to do.  Thanks.  Sorry for being such a noob.

---

### Post by solar george on 2007-02-19
Go to the 'System' menu then to preferences them desktop background. This will open a tool that you can use to change the desktop background settings. You will probably need to change the option that is set at centred to scaled. This should help

---

### Post by sloggerkhan on 2007-02-19
1st off, desktop background: right click on desktop, click change background, and change style. (stretch, zoom, etc.) That's most likely the issue if the problem is ONLY the desktop background. (if it is a laptop and the border is COMPLETELY black with no panel, are you using a dell?)

ok. ATI drivers can be a problem.
So first open a console window.
Use the following command:
sudo gedit /etc/X11/xorg.conf


This command opens what amounts to the graphics card's configuration file with root, or administrative, access. This file can control many features and aspects of your displays and graphics cards and is often misconfigured by default, expecially on newer ATI cards. (at least in my experience.)

Check and see what the 
Section "Device" 
has as options.

Example:
Section "Device"
	Identifier	"Ati x700"
	Driver		"fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID		"PCI:1:0:0"
EndSection

If yours says ATI where the above says fglrx, you are using the open source Radeon/Ati driver, and should switch to the ATI closed source driver, or FGLRX, if you have a card that is newer than an x700 or 800. If you go to FGLRX, you will need to install it from repos or ATI website.

If your card is pre-x series or even an x700 or so, ATI driver is USUALLY ok. 

To get the additional screen resolutions you want, under the "screen"  section in "display" subsections add additional resolutions up to your max res, following format.

If you have more detailed info, I might be able to help you more.

---

### Post by Flufflebuns on 2007-02-19
Sorry I forgot to make specific.  Yes I happen to be using a dell laptop, and I'm definitely not SO aloof that wouldn't know the difference between the background and the actual desktop.  Sorry I should have made that clear, the desktop background fits the screen (at least to the taskbars top and bottom) but the black border is outside all that, like the full screen is shrunk.  This is why I think it's a resolution problem.

In the config menu for xorg I tried to hit the new parameters for resolution, but for some reason it won't register.  What I mean is when I check the 1600x1200 box during setup it won't register in the Screen Resolution Preferences, it still gives only three options.  (Even after restart).  I'll try all the other suggested stuff, though I'm having trouble finding a specific ATI Mobility Radeon M4 driver, should I download a generic Linux ATI driver?  And from where?

Thanks for quick help all!

---

### Post by sloggerkhan on 2007-02-19
Your problem relates to dell hardware I am almost 100% sure. I have seen on at least 4 dell notebooks running a variety of OSes (thought mostly windows.) where any resolution below max res will not stretch to fit screen. Consequently, you must run under max res for the whole screen to work. That aspect of the problem is dell related and you should take it up with them.

However, my experience with this issue is that you can get Max resolution working and filling the whole screen. So that aspect of your problem should be fixable.

I didn't mean to imply you were aloof, I just wasn't clear on what you were having trouble with.

The M4 is an older ATI chip? about Rage 128 era? I haven't really heard of an M4.

If so, it might be that newer fglrx drivers don't support it. I am not sure.
Could you post your xorg.conf file?

---

### Post by Flufflebuns on 2007-02-19
Sorry, I've been busy today.  And don't worry I was offended at all about the aloof thing.  Anyway I can't get the internet to work right on my Ubuntu computer either, but that's a whole other story.  So I had to transfer the info from there to this comp via a flash drive.  Here's my xorg info:

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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
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
	Identifier	"ATI Mobility Radeon M4"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-80
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Mobility Radeon M4"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


Thanks a ton for all the help.  This seems a lot more challenging than I expected!

---

### Post by sloggerkhan on 2007-02-19
vesa is not a good driver. I'd say it's the linux version of software rendering. That's probably why you can't get the screen resolution you'd like.

Not sure what I can do. I'll look around when I have some free time and see if I can find any correct drivers for your devicesomewhere.

ATI cards are a little annoying in general, and it doesn't help that yours seems to be a relatively uncommon model from around year 2000 which it looks like ubuntu doesn't autodetect a driver for. So yeah, more challenging for sure. lol.

---

### Post by solar george on 2007-02-20
What is the output of

```
lspci
```
?

---

