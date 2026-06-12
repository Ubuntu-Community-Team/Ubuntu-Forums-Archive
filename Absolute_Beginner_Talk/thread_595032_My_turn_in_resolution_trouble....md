---
title: "My turn in resolution trouble..."
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by Innernet on 2007-10-28
Downloaded 7.10, burned CD, checked integrity, installed...  went smooth, I think.

Changed the resolution from 1280 x 1024 -75 Hz to 60Hz and image became beautifully centered.
Well, next day back to the same shifted and off border image after boot.  Now when I try to do the same change operation with System>preferences>screen resolution OR System >administration>screens, nothing changes, 'keep resolution' or 'use previous' do nothing either.:confused:
Manually trying to drag the frame to proper position, it does not move at all :confused:

Running an Intel D845GVSR mommyboard with built-in video and Celeron D325.   My other 7.04 hard drive works perfectly well with it.

Also, 7.10 does not recognize my USB HP series 4300 printer ;  and downloaded VLC stream player does not work. Fine on the 7.04 hard drive.

What have I done wrong ?  Seen many, too many resolution problems in previous posts...:(

---

### Post by Pumalite on 2007-10-28
Memory?.

---

### Post by Innernet on 2007-10-28
System monitor shows 502 MB

---

### Post by Pumalite on 2007-10-28
You have memory to boot a Live CD, but with your graphics, I'd install with Alternate CD.
(also integrated graphics eats into your available memory)

---

### Post by Innernet on 2007-10-28
Rebooted 7.10 : The initial screen with the orange bars showed, then a monitor generated message  shows "Too high frequency" ; stuck on a blackout screen.

What a joke !
In that blackout screen condition, what am I supposed to do to change resolution settings ????
This looks like made either for too intelligent geniuses, or an imitation to  Mr. Gates strategy.

Removed the 7.10 hard drive, installed the 7.04  one to be able to post this.  Works fine.
Again, better said, what a disapointment !

---

### Post by Innernet on 2007-10-28
The only choice in front of me was to install again 7.10 as I was stuck with this black screen...

By the way, that means losing ALL FILES right ???  Or there is a way ????

Plugged in a different monitor as last resource; same message : Frequency out of range.
Rebooted, and was a second late to insert the 7.10 LiveCD in the drive in order to reinstall and the hard drive took over again... surprise!  screen back to normal.

This is for too intelligent geniuses.  I have no explanation. :confused:
(Posting this message with 7.10)

Thanks for the good intention, guys.

---

### Post by daimaru on 2007-10-28
just edit your /etc/X11/xorg.conf file and change your resolution to whatever you want . 

post your xorg.conf will help determining problem
EDIT: ok if your stuck at black screen hit ctrl+alt+f2 then login at terminal type sudo nano /etc/X11/xorg.conf change your section screen to something that fits what you want.
heres mine 

```

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G80 [GeForce 8800 GTS]"
        Monitor         "Samsung SyncMaster 214T"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600"
        EndSubSection
EndSection



```

---

### Post by Innernet on 2007-10-28
Thanks, daimaru.

But how do I   ...."edit your /etc/X11/xorg.conf file and change your resolution to whatever you want"...

With a monitor that was displaying nothing ?   Or you mean do it now?

---

### Post by dhughes on 2007-10-28
You may not realize but you have several "screens" you can use not just the GUI you were trying to set up. Press ctrl+alt+F1 to see one called tty1, you can also try F2, F3, F4, F5 and F6. If you go ctrl+alt+F7 that is the graphical user interface. You can have all seven doing something if you want.

 If you have trouble with the GUI (tty7 I guess it is) you could try ctrl+alt+BACKSPACE to stop (kill) the GUI or "xserver" as it is properly called I guess .

 To reconfigure your GUI or xserver I believe you use the command:
 ```
 sudo dpkg-reconfigure xserver-xorg
``` and follow the steps, it would be good to know your monitor and video card's specs beforehand. Such as your monitor's horizontal and vertical refresh rates and your video card's supported resolutions.

 The newly designed video card setup utility threw me for a bit there are two sections and I was confusing what was what but now I have it set OK, maybe that was what your trouble was initially?

---

### Post by daimaru on 2007-10-28
> **Innernet said:**
> Thanks, daimaru.

But how do I   ...."edit your /etc/X11/xorg.conf file and change your resolution to whatever you want"...

With a monitor that was displaying nothing ?   Or you mean do it now?

plz post your xorg.conf file then i might be able to help you more specifically , and as i said before if you only get terminal use nano to edit xorg.conf change the "modes" line to "1024x768" "800x600" if you only want those 2 resolutions xserver picks the first one in the line as default

if your monitor displays nothing hit ctrl + alt + f2 or f1 
that should put you into console mode but if that does not work something way more serious is the problem . meaning your monitor does not work at all .

---

### Post by Innernet on 2007-10-28
Is this what you are asking for ?:

==================================================

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
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Boardname	"intel"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1600	1200
		Modes		"1280x1024@60"	"1280x960@75"	"1280x960@60"	"1400x1050@60"	"1280x1024@75"	"1600x1200@60"	"1152x864@75"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
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
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection

======================================================

As in message #6 -> all became normal by itself.

---

### Post by Innernet on 2007-10-28
Had to cool down with a shower...  Then, turned the compfuser on again, and the same story.  The black screen of death. 
It happens after the initialization orange bars show up.  That is, when the login and password are to be entered.

As I know it's time to type, just blindly did it and the display appears and behaves normal again.

Then, in my total ignorance of these things, I believe the resolution for the login screens goes bananas.

Why?  Guessing... because the whatever sets the chosen resolution has not executed yet ? Or there is resolution settings for different screens ?
I would need a brain to fix it.

Suggestions written in idiot proof language please ?

---

### Post by dhughes on 2007-11-12
I had a similar problem, I think, after I fiddled around with my resolution trying to see if I could make it better (it drags a bit on my old system).  Anyway I did something wrong and it's similar to your problem.

  I ended up getting it to work by choosing Screen 1 listed under the Screens tab section for some reason Screen 2 was selected as my default screen and I couldn't change it from its default 800x600 75Hz resolution.

  Under the Graphics Card tab it already had my driver there so I left that alone, actually there were two sections my card driver was the top one and the bottom one was for the VGA driver.

  I also clicked the save icon and gave what I did a name I guess it's sort of a config file, I named it but I don't know if that was necessary.

  I had to log off and back on but after that it was fine.

---

