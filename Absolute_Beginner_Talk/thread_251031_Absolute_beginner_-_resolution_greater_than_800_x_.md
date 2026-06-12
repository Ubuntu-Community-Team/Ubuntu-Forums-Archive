---
title: "Absolute beginner - resolution greater than 800 x 600"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by snteran on 2006-09-04
I am brand new to Ubuntu and to Linux.  I recently install the O/S and have only two option for my screen resolution - 640 x 480 and 800 x 600.  I would like to increase to 1024 x 768 but I'm not sure how to do that in Linux.  I am a windows person, but I do want to see what Linux offers and try to learn something totally new.  I was going to download Everest to view what video card I had to perhaps find a driver to install to help increase resolution but I don't see everst for linux and then I would have no idea to install the driver.  Any help would be great, even if you could tell me how to find out what version of Ubuntu I installed.

Thanks

---

### Post by greyash99 on 2006-09-04
[http://www.ubuntuforums.org/showthread.php?t=250285&highlight=resolution](http://www.ubuntuforums.org/showthread.php?t=250285&highlight=resolution)

---

### Post by taurus on 2006-09-04
Open a terminal and at the prompt, just type

```
lspci
```

---

### Post by Crashmaxx on 2006-09-04
Click on System>Preferences>Screen Resolution and change it there to whatever you want. If that doesn't work or is what you already tried then try this.

Open the file /etc/X11/xorg.conf and look in the "Device" and "Screen" sections. Device should tell you what graphics card and driver you have, and screen should say what resolutions and color depths. Post those sections here and I'm sure someone can help.

Good luck, and welcome!

---

### Post by szf on 2006-09-04
>> What version of ubuntu?

Maybe try 
[FONT="Fixedsys"]less /proc/version[/FONT]

>> What hardware?

Maybe try 
[FONT="Fixedsys"]less /var/log/messages | grep vid[/FONT]

Help us, ubuntu forums?

---

### Post by snteran on 2006-09-04
Looks like a lot of great information.  Thank you for all the help.

---

### Post by snteran on 2006-09-04
It appears that the desired screen resolution is listed but not showing up as an option for 1024 x 768.  I am running two computers with the use of a kvm switch.  I have windows on one computer and Ubuntu on the other.  Windows has many resolutions to which to choose from, so I can only imagine that I should be able to get those from the Ubuntu box.  I am posting the requested section of my file.


Section "Device"
	Identifier	"ATI Technologies, Inc. Mach64 VT (264 VT)"
	Driver		"ati"
	BusID		"PCI:0:20:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Mach64 VT (264 VT)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
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
EndSection

Section "DRI"
	Mode	0666
EndSection

Please let me know if more information.

Cheers

---

### Post by Crashmaxx on 2006-09-05
Ok, the first thing I notice is the ATi card with the ati driver. This is a generic driver that won't support 3D or in general make good use of your graphics. So I would suggest upgrading it to the fglx driver. This may not fix this specific problem, but it is a good idea in general. Though you may want to skip it for the moment and try the next couple things first, depends how much the resolution bothers you. So here is that how-to:
[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)

The next thing I noticed was that you said you use one monitor with a switch for both machines. I have noticed before that if my monitor is off and I boot the computer the resolution may be screwed up. I guess it didn't detect the monitor and went for a lower resolution. This is an easy thing to test. Either just reboot the computer and make sure the monitor is on and switched to the ubuntu machine. Or have the ubuntu machine running with the monitor on and switched to the ubuntu machine and press CTRL+ALT+BACKSPACE. This will restart just your graphics session and may fix the problem. It will also restart all your programs, so save and close them first. If you do that and it does nothing, then reboot. This just a quicker way then rebooting but not as likely to fix the problem.

Anyway, the last thing I notice is that it says "Generic Monitor". And your resolutions seem to be setup correctly. So what could be happening, that even though 1024x768 is the default, the settings for "your monitor" aren't enough to run that, so it goes to the next best 800x600. So if you could look up the model of monitor you use and find its specs, you should just need to know the refresh rate, and its horizontal sync and vertical refresh rate. Put those values into the monitor section instead of the current ones and it may fix your problem.

If none of that works, then I'm sorry, hopefully someone else knows. And if you have any questions, feel free to ask.

---

### Post by snteran on 2006-09-06
Well, thanks for the info.  I was able to find information on my monitor ( G773 ViewSonic).  1280x1024 maximum resolution
Displays a maximum resolution of 1280x1024; 1024x768 optimal resolution at 87Hz flicker-free refresh rate for easy-on-the-eyes viewing.
1280x1024 @ 66Hz
1024x768 @ 87Hz
800x600 @ 110Hz
INPUT SIGNAL  	Video  	RGB analog (0.7Vp-p, 75 ohms)
Sync 	H/V separated (TTL), composite
Frequency 	Fh:30-70kHz, Fv:50-180Hz

However, I believe I am still stuck because my files are coming up as read only.  I tried to login as root but I did not create a root password.  Actually I was never given a prompt to create a password for root.  So I guess I need to find out how to connect as root first and then I think I can install the fglx driver and then edit the xorg.conf file as needed.
Any advice on getting root going, please let me know.

thanks,

---

### Post by bodhi.zazen on 2006-09-06
> **snteran said:**
> Well, thanks for the info.  I was able to find information on my monitor ( G773 ViewSonic).  1280x1024 maximum resolution
Displays a maximum resolution of 1280x1024; 1024x768 optimal resolution at 87Hz flicker-free refresh rate for easy-on-the-eyes viewing.
1280x1024 @ 66Hz
1024x768 @ 87Hz
800x600 @ 110Hz
INPUT SIGNAL  	Video  	RGB analog (0.7Vp-p, 75 ohms)
Sync 	H/V separated (TTL), composite
Frequency 	Fh:30-70kHz, Fv:50-180Hz

However, I believe I am still stuck because my files are coming up as read only.  I tried to login as root but I did not create a root password.  Actually I was never given a prompt to create a password for root.  So I guess I need to find out how to connect as root first and then I think I can install the fglx driver and then edit the xorg.conf file as needed.
Any advice on getting root going, please let me know.

thanks,


LOL. Ubuntu uses "sudo" by default.

Thus to run a command as root, in a terminal,
```
sudo <command>
```
You will be prompted for a PW, use your regular user password (the one you use to log into Ubuntu).

To run a graphical progarm, use gksudo

ie: gksudo nautilus.

---

### Post by snteran on 2008-04-03
OK, so I'm back for more pain.  I gave up on trying to fix the screen resolution and now I have decided to try to learn once again how to operate a Linux OS.  The main reason was to utilize Nagios which I have successfully installed with much help from the forums.  I did the steps above and I think I installed the new Fglrx drivers, I say think because I'm still having the same problem of only having 800 x 600 for a screen resolution.  I have gotten rid of my kvm swith and switched to a dual boot.  XP works fine and I need to get Linux working correctly.
When I start Ubuntu, I always get a prompt that Ubuntu is running in Low-graphic mode, I choose configure and select my Viewsonic G773 with a resolution of 1024x768 but it always defaults to 800x600.  How can I verify that the Fglrx driver is installed.

Here is what I have in my xorg.conf file:
```


# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
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

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"ATI Mach64"
	Busid		"PCI:0:15:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"ViewSonic"
	Modelname	"ViewSonic G773"
	Horizsync	30-70
	Vertrefresh	50-160
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
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1400	1050
		Modes		"1024x768@43"	"1152x864@75"	"1024x768@60"	"1280x960@60"	"1024x768@70"	"1280x1024@60"	"1024x768@75"	"1400x1050@60"	"1024x768@85"	"832x624@75"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"Matrox Millennium G200"
	Busid		"PCI:1:0:0"
	Driver		"mga"
	Screen	0
	Vendorname	"Matrox"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

```
Thanks for the help.

Determined user!

---

