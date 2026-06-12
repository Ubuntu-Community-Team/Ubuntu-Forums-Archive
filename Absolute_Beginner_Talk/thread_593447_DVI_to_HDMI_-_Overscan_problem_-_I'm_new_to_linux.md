---
title: "DVI to HDMI - Overscan problem - I'm new to linux"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Dirtydozen on 2007-10-27
Hi there!

I'm new to linux and appreciate all the help I can get on this.

I have a 37" LCD TV, the native resolution is 1360x768, HD720p. I have a Nvidia Geforce 6200 256MB, ubuntu 7.10.

Problem:
When I use the VGA port everything works, but when I'm using DVI to HDMI, the screen stretches and I miss some of the left, right, top and bottom. This works fine in Windows XP, but I would hate to go back to windows just because the overscan problem.

I have installed Nvidia restricted drivers, but nvdia-settings, don't help and it don't matter what resolution I set, I get same problem. But I can't get to choose 1360x768, that's the native resolution.

I have read this:
[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.09/README/chapter-16.html](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.09/README/chapter-16.html)

But where in my xorg.conf should I put(and will it help?):
    Option "TVStandard" "HD720p"
    Option "UseDisplayDevice" "TV"


**XORG.CONF:**
Section "Device"
	Identifier	"nVidia Corporation NV44A [GeForce 6200]"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Sigma Tango"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1360x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV44A [GeForce 6200]"
	Monitor		"Sigma Tango"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	768
		Modes		"1280x768@60"	"1280x720@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "device" #      
	Identifier	"device1"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	1
EndSection
Section "screen" #      
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"	"640x480@72"	"640x480@75"	"640x480@85"	"800x600@56"	"800x600@72"	"800x600@75"	"800x600@85"	"800x600@60"	"832x624@75"	"1024x768@75"	"1024x768@70"	"1024x768@60"	"1280x960@60"	"1280x1024@60"
	EndSubSection
EndSection
Section "monitor" #      
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by mrazvan on 2007-11-02
I have exactlly the same setup (DVi -HDMI cable) and problem just at a different resolution 1920X1080, HD1080p. 

I've added under -Section "Screen"- in /etc/X11/xorg.conf :
Option "TVStandard" "HD1080p"
Option "UseDisplayDevice" "TV"

....with no effect. I'm still missing some of the left, right, top and bottom of the screen.

Any suggestions?

Thanks!

---

### Post by Yfrwlf on 2008-05-22
Until either Nvidia or the open source drivers implement some kind of overscan adjustment (unless the open source drivers or X already can do this, but a GUI option has yet to be implemented), I think we may be out of luck with this problem.  The only way I was able to correct this issue is by finding a setting on my TV to change it.  I read that one such TV option was called "Full Pixel", and when enabled gave them a perfectly-fitted picture on the screen.  Lucky them!  I was not as lucky.  I have a Mitsubishi DLP 73" 1080p TV, and for a while I simply made the size of the Gnome panels bigger, along with the fonts so that everything was more visible (probably will have to increase font sizes regardless, since 1920x1080 is such a large desktop).  Then, I discovered the "FORMAT" button on my remote control.  This allowed me to switch from "Standard" mode to "Reduce" mode, so now I can see my full desktop.  It doesn't perfectly fit into the TV frame, I do have some small black boarders, but that's OK by me, especially since DLP TVs have no problem with burn-in among other things, the only thing you have to worry about is bulb replacement and finding a cheap bulb, unless it's all proprietary and locked down, which would suck.  The user who had the "Full Pixel" option was using a Sony TV.  Perhaps that will be my next TV unless Mitsubishi gets their act together.  I mean, come on, there's no reason not to have instant full and perfect picture with any of the following (I think) HDMI, DVI, component, or VGA inputs, since TVs are practically the same thing as monitors now days.  I don't think ATI has an overscan mode in their proprietary closed driver, either, and no doubt it's lacking in the open ones too.  Sheesh these companies need to get their act together.  Or, maybe they won't have to if TVs get *their* act together and stop having an issue with fitting PC resolutions onto the screen.

---

