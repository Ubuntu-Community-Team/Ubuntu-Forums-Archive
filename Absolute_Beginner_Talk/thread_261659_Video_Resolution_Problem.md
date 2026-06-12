---
title: "Video Resolution Problem"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by Eutychus on 2006-09-20
Hi ... complete newbie here, so there's probably something very simple that I'm missing.

Running : ASUS P4V8X-MX motherboard
          Intel Celeron precessor 
          Hewlett Packard vs17e monitor

The monitor support 1280x1024 screen resolution but I prefer 1024x68. The problem is that I go to Preferences > Screen Resolution and select 1024x768 and click the little box that says it should be the default for my system. But when I click apply, the screen blanks for a second, and then the system bumps back to the log in screen and I'm still at 1280x1024. It somehow is not accepting the screen resolution that I want. What should I be looking at?

---

### Post by dhruv_1884 on 2006-09-20
Hi,
Got to the Termianl (Applications>Accessories>Terminal) and run the command
```
sudo dpkg-reconfigure xserver-xorg
```

a program designed to set up your hardware starts, it has long descriptions and plenty of questions which are quiet easy to understand and answer,so please put in some time to read them

once the configuration program exits ,  press 
Ctrl+Alt+Bkspc


This shud work.

---

### Post by bodhi.zazen on 2006-09-20
As a first step:```
sudo dpkg-reconfigure -phigh xserver-xorg
```Is easier and the first step.

-phigh is the key to simplification.

---

### Post by Eutychus on 2006-09-22
Neither suggestions worked.

Each time I try it kicks me to the non-graphics log-in and says "Failed to Start the X-server." I'm using the via video chip but even going through the whole thing using the default settings, it kills the x-server.

Right now I'd be happy just to be able to get back to the graphics interface without having to do a complete re-install.

---

### Post by bodhi.zazen on 2006-09-22
Error message?

---

### Post by Eutychus on 2006-09-22
Noe that I can see. It just says "Failed to Start the X-server. It is likely it is not set up correctly. Would you like to view the x-server output to diagnose the problem?"

---

### Post by bodhi.zazen on 2006-09-22
And when you "view the x-server output to diagnose the problem?" what does it say?

---

### Post by Eutychus on 2006-09-22
> **bodhi.zazen said:**
> And when you "view the x-server output to diagnose the problem?" what does it say?

Here goes :

X WINDOWS SYSTEM VERSION 7.0.0
RELEEASE DATE 21 DECEMBER 2005
X PROTOCOL VERSION 11, REVISION 0 RELEASE 7.0
BUILD OPERATING SYSTEM LINUX 2.6.15.7, i686
CURRENT OPERATING SYSTEM LINUX xxxx-desktop 2.6.15-27-386 #1 PREEMPT

SAT SEP 16 01:51:59 utc 2006 i686

BUILD DATE : 16 March 2006

  Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
  to make sure you have the latest version

MODULE LOADER PRESETS

MARKERS (--) probed, (**) from config file, (==) default section,
   (++) from command line, (!!)notice, (!!) information

(==) Log file "/var/log/xorg.0.log", time fri sep 22 19:15:52 2006

(==) using congfig file "/etc/X11/xorg.conf"

Thanks for your patience with me.

---

### Post by ReaderRat on 2006-09-22
I have noticed that, if you are trying to change the resolution while running a Live CD copy, it will not work for me either. But, when I actually installed ubuntu on my hard drive, it worked fine.

---

### Post by bodhi.zazen on 2006-09-22
> **Eutychus said:**
> 

(==) Log file "/var/log/xorg.0.log", time fri sep 22 19:15:52 2006

(==) using congfig file "/etc/X11/xorg.conf"

Thanks for your patience with me.

Not much there.

can you post ```
cat /var/log/xorg.0.log
```

---

### Post by Eutychus on 2006-09-23
> **bodhi.zazen said:**
> Not much there.

can you post ```
cat /var/log/xorg.0.log
```

Contens of xorg.0.log :

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux xxxx-desktop 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Sep 23 05:20:01 2006
(==) Using config file: "/etc/X11/xorg.conf"
Data incomplete in file /etc/X11/xorg.conf
	Undefined Device "Generic Video Card" referenced by Screen "Default Screen".
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found
(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor

Also, here is the contents of xorg.conf to cross reference it by :

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
	Identifier	"Generic Video Card"
	Driver		"vga"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"HP vs17"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"HP vs17"
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
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


I'm headed to work now, so I'll pick this back up later this afternoon.

Thanks again!

---

### Post by bodhi.zazen on 2006-09-23
Thanks.

Nice work listing xorg.conf, that would have been the next question, I should have included that information on my request.

Unfortunately after looking at your file I can not see anything wrong with it. My only thought is your PCI value is off:> Section "Device"
Identifier "Generic Video Card"
Driver "vga"
**BusID "PCI:1:0:0"**
EndSection

try:
```
lspci
```

This will list your PCI devices. If that list is too long, try

lspci | grep VGA

Make sure your vidio card has a PCI of 01:00.0.

Note the format of the numbers is different,
lspci = xx:yy.z

and

xorg.conf = x:y:z

On my box> bodhi@Arch:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0391 (rev a1)
bodhi@Arch:~$ grep 'PCI' /etc/X11/xorg.conf
        BusID           "PCI:1:0:0"

HTH or someone more knowledgable then I can help. [-o<

---

### Post by Eutychus on 2006-09-23
Well, it didn't work. The PCI values are correct.

Me sad puppy.

But I guess it could be worse. The system is working well except for the video resolution problem.

But now on looking deeper, I see that the setup disc for my chipset has linux drivers on it, but only for Mandrake, RedHat and SUSE; none for Debian. Is there something here that maybe should be investigated?

---

### Post by Eutychus on 2006-09-24
I did a fresh install and went back into xorg.conf with nano and edited out the "1780 x 1024" tag under the 24 depth of the monitor setting. Restarted and it's fine now! I could have sworn i'd done that before but apparently I was missing something somewhere.

Thanks for all your help! It's certainly been a learning experience, but then, i guess that's part of what all of this is about!

---

