---
title: "Aspect Ratio on Acer Travel Mate 4101 Widescreen"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by ramjet_1953 on 2006-09-13
Hi, Guys!

I know that this topic has been talked about many times before and I have looked at the various postings. I still can't get my laptop into widescrren mode and this is the only thing preventing me from changing over to Ubuntu completely.

I downloaded 915 resolution and then ran 915resolution -l
See attachment for listing

I then ran 915resolution 62 1280 800

I then re-booted and when I went into Preferences - Screen Resolution, the maximum resolution was stiil only 1024 X 768.

I have also attached a copy of my xorg.conf file and the screen resolution information when I am running under Windows XP.

I hope that this can be resolved as I need the correct aspect ratio as I use my PC for CAD and photographic work.

Regards,
Roger:???:

---

### Post by ramjet_1953 on 2006-09-13
No takers on this yet?

Regards,
Roger:?

---

### Post by ramjet_1953 on 2006-09-14
Is this one in the "TOO HARD" basket?

Regards,
Roger :-?

---

### Post by ramjet_1953 on 2006-09-14
I'm still waiting on some help with this.
I know it is a common problem with widescreen LCD's, but is is essential for me that I get the aspect ratio right as I want to use CAD software.

Regards,
Roger 8-)

---

### Post by fragos on 2006-09-15
Look at /etc/X11/xorg.conf and see if the video driver is "vesa".  Do an lspci in a terminal window to see which video chip set is used.  It may be "sis" as it is on an Acer Aspire 3004.  It has 1280x800 resolution but I couldn't get it to work.  The owner of the laptop has it now and is happy the way it is.  I didn't get to try this if I get that loptap back I plan to try changing the driver from "vesa" to "sis".  Let us know if this works.

---

### Post by ramjet_1953 on 2006-09-15
Thanks for the reply!

lspci says I have the following graphics chipset:

Intel Mobile 915GM/GMS/910GML

My /etc/x11/xorg.conf file says my video driver is i810

Regards,
Roger :)

---

### Post by fragos on 2006-09-15
I would think that the driver might only use resolutions its familiar with.  The identified monitor might be the real determinant of what resolutions the driver will try.  With Nvidia cards and 3D driver I've been able to change resolutions in xorg.conf, including a wide screen 1440x900 for my VA1912 wb LCD monitor.  In my xorg.conf my monitor is set to the generic default set by Linux.  I'm afraid my success with my systems has limited further experimentation and learning.

---

### Post by ramjet_1953 on 2006-09-15
Still no joywith this!
Surely someone must have had the same issue with an Acer TravelMate?
I would really like to stick with Ubuntu, but as I need the correct aspect ratio for CAD and photographic work, I will have to go back to XP if it can't be sorted.

Regards,
Roger :cool:

---

### Post by fragos on 2006-09-16
I wish I had an answer for you.  Have you tried [http://www.linuxquestions.org](http://www.linuxquestions.org).  It's a great forum for Linux questions and they have a forum specifically for Ubuntu.  IMHO this sounds more like an Xserver video driver issue and it may get better expert coverage at Linuxquestions.org.  Acer as company has a good reputation with Linux.  I'd try their support forums as well.  Perhaps if you ask the question relative to wide screen video in general you will get better response.  When you find an answer please post it in this thread.  I and others would love to know the answer so I can help others.  Best of luck, I'll keep my eyes open for an answer for you as well.

---

### Post by fragos on 2006-09-16
I believe I found a solution for you.  Run the following on the command line:

sudo dpkg-reconfigure xserver-xorg

This will run a terminal based xserver configuration which will amongst other things, give you the option to select which resolutions you wish to use.  I ran it on my system and got excellent results except that it selected the open source "nv" driver for my nvidia card.  I just edited it to use "nvidia" the 3D driver I had separately installed.  When it exits it saves your old xorg.conf so you can compare them if you like and even backup to the original.

---

### Post by ramjet_1953 on 2006-09-16
Hi, George!

Already done all of that, with no success.
I even downloaded KDE Desktop, as it has more powerful user-friendly graphics configuration utilities.
I ran the KDE utility, it auto detected that I had a 16:9 monitor, that I had an Intel 915 chipset. I thought, great, I'm there. But when I re-booted, it was even worse! I now only had 800X600 resolution, even though the auto detect utility said I could operate in 1280X800 at 24 bit!
What I can't understand is that the forums are full of problems along these lines. With all the geeks involved in Linux, surely a simple thing like setting screen resolutions is not too much to ask?
Under XP, it's just a couple of clicks and all done.

Regards,
Roger :cool:

---

### Post by fragos on 2006-09-16
X configuration is a problem area.  It usually works just fine but sometimes not.  X needs to play catchup with the rest of Linux.  It is being worked on but there seems to be some hangups because not all video drivers are open source.  I hope your problem gets resolved soon.  If I get any more ideas I'll post them.  -- George

---

### Post by ramjet_1953 on 2006-09-20
Whoop!
Finally worked it out!
Typical engineer that I am, I was trying all sorts of complicated things, like trying to force the bios, etc.
All it took was to clear everything out of the xorg.conf file that didn't relate to 1280x800 24 bit and just leave the one entry.

Here is a listing for those who may also have an Acer TravelMate 4100.

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
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/Type1"
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
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option	"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
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
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


I also did this in a terminal:

915resolution 3c 1280 800 24

This just replaced an unwanted resolution with the one that I wanted for the correct aspect ratio.

As a side benefit, it also foxed up the problem with some really yuccky fonts that I was getting with a couple of applications, namely GNU Cash and Audacity.
The great thing is that I am now in a position to say goodbye to Redmond forever!

Regards,
Roger :D

---

