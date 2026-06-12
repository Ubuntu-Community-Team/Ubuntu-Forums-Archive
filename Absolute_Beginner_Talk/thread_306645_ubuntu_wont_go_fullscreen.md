---
title: "ubuntu wont go fullscreen"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by Bad Apple on 2006-11-25
I have installed ubuntu as a second OS on a samsung V20

I am using an external monitor (Dell D1526TX-HS) as the samsung display is dead. The samsung has an Intel 845GL 64mb onboard video card.

When in Windows the dispay works fine, but when I am in ubuntu, the display refuses to use the whole of the screen, staying centre of the screen at roughly half size

can anyone help? i have tried a lot of different things out, from varius forums, but none have come to fruition of yet

thank you ](*,)

---

### Post by taurus on 2006-11-25
Did you install "815resolution" driver for your graphic card?

---

### Post by bodhi.zazen on 2006-11-25
> **Bad Apple said:**
> I have installed ubuntu as a second OS on a samsung V20

I am using an external monitor (Dell D1526TX-HS) as the samsung display is dead. The samsung has an Intel 845GL 64mb onboard video card.

When in Windows the dispay works fine, but when I am in ubuntu, the display refuses to use the whole of the screen, staying centre of the screen at roughly half size

can anyone help? i have tried a lot of different things out, from varius forums, but none have come to fruition of yet

thank you ](*,)

I recently had the same problem, but on a DELL. The fix was to edit xorg.conf and re-start X.....

[See this post for details](http://ubuntuforums.org/showpost.php?p=1799642&postcount=15)

---

### Post by Bad Apple on 2006-11-25
taurus: dont think so

so to be so dumb, but how do i do that?

bodhi: done alot of that, nothing has worked thus far

---

### Post by bodhi.zazen on 2006-11-25
> **Bad Apple said:**
> taurus: dont think so

so to be so dumb, but how do i do that?

bodhi: done alot of that, nothing has worked thus far

The only other potential solution is to try to update your bios.

---

### Post by taurus on 2006-11-25
When you open synaptic from System -> Administration, you will see 815resolution package on it.  Install it and modify your /etc/X11/xorg.conf to use that driver instead of probably vesa right now!

---

### Post by Bad Apple on 2006-11-25
i would like to try this 815resolution thing, how do i do that?

and can i update bios with out uninstalling either of my os's?

---

### Post by bodhi.zazen on 2006-11-25
> **taurus said:**
> When you open synaptic from System -> Administration, you will see 815resolution package on it.  Install it and modify your /etc/X11/xorg.conf to use that driver instead of probably vesa right now!

I think the package you are referring to is 915resolution.

815resolution is now a "virtual package" within 915resolution.

If you install 915resolution you will need to configure it. I have some instructions on how to do this [here](http://ubuntuforums.org/showthread.php?t=269052)

Sorry it is a long thread, scroll down to the 915 resolution section under videocards.

---

### Post by bodhi.zazen on 2006-11-25
> **Bad Apple said:**
> i would like to try this 815resolution thing, how do i do that?

and can i update bios with out uninstalling either of my os's?

Yes you can update the bios without uninstalling either OS. You need to see if there is a bios update available from Dell:

[Dell update BIOS](http://www.bay-wolf.com/flashbios.htm)

The bios update is run from windows....

Install 915resolution from synaptic and configure.....

---

### Post by Bad Apple on 2006-11-25
i cant find 915resolution?!?!

---

### Post by bodhi.zazen on 2006-11-25
> **Bad Apple said:**
> i cant find 915resolution?!?!

Add some repositories:

```
sudo gedit /etc/apt/sources.lst
```

Remove the # in front of you sources, so it looks ilke this:

> deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

then:```
sudo aptitude update && sudo aptitude install 915resolution
```

---

### Post by Bad Apple on 2006-11-25
done that, this is what it says. looks to me like it failed?!?!

```
Reading package lists... Done
Building dependency tree... Done
Initialising package states... Done
Building tag database... Done
Get:1 http://gb.archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://gb.archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:3 http://security.ubuntu.com dapper-security Release.gpg [191B]
Get:4 http://gb.archive.ubuntu.com dapper-backports Release.gpg [191B]
Hit http://gb.archive.ubuntu.com dapper Release
Hit http://security.ubuntu.com dapper-security Release
Hit http://gb.archive.ubuntu.com dapper-updates Release
Hit http://security.ubuntu.com dapper-security/main Packages
Get:5 http://gb.archive.ubuntu.com dapper-backports Release [23.3kB]
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Get:6 http://security.ubuntu.com dapper-security/universe Packages [41.4kB]
Hit http://gb.archive.ubuntu.com dapper/main Packages
Hit http://gb.archive.ubuntu.com dapper/restricted Packages
Hit http://gb.archive.ubuntu.com dapper/main Sources
Hit http://gb.archive.ubuntu.com dapper/restricted Sources
Get:7 http://gb.archive.ubuntu.com dapper/universe Packages [2458kB]
Get:8 http://security.ubuntu.com dapper-security/universe Sources [5094B]
Get:9 http://gb.archive.ubuntu.com dapper/universe Sources [975kB]
Hit http://gb.archive.ubuntu.com dapper-updates/main Packages
Hit http://gb.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://gb.archive.ubuntu.com dapper-updates/main Sources
Hit http://gb.archive.ubuntu.com dapper-updates/restricted Sources
Get:10 http://gb.archive.ubuntu.com dapper-backports/main Packages [11.5kB]
Get:11 http://gb.archive.ubuntu.com dapper-backports/restricted Packages [14B]
Get:12 http://gb.archive.ubuntu.com dapper-backports/universe Packages [34.3kB]
Get:13 http://gb.archive.ubuntu.com dapper-backports/multiverse Packages [2430B]Get:14 http://gb.archive.ubuntu.com dapper-backports/main Sources [3644B]
Get:15 http://gb.archive.ubuntu.com dapper-backports/restricted Sources [14B]
Get:16 http://gb.archive.ubuntu.com dapper-backports/universe Sources [8317B]
Get:17 http://gb.archive.ubuntu.com dapper-backports/multiverse Sources [1058B]
Fetched 3564kB in 1m42s (34.7kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Initialising package states... Done
Building tag database... Done
The following packages have been kept back:
  libtag1c2a libtheora0 readahead
The following NEW packages will be installed:
  915resolution
0 packages upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 14.3kB of archives. After unpacking 127kB will be used.
Writing extended state information... Done
Get:1 http://gb.archive.ubuntu.com dapper/universe 915resolution 0.5-1ubuntu6 [14.3kB]
Fetched 14.3kB in 1s (8046B/s)
Selecting previously deselected package 915resolution.
(Reading database ... 72473 files and directories currently installed.)
Unpacking 915resolution (from .../915resolution_0.5-1ubuntu6_i386.deb) ...
Setting up 915resolution (0.5-1ubuntu6) ...
Starting 915resolution: Panel id function not supported
*** Your 915resolution was not automatically configured! ***
Please read /usr/share/doc/915resolution/README.Debian then define
MODE, XRESO, and YRESO manually in /etc/default/915resolution or install 'vbetool'.
invoke-rc.d: initscript 915resolution, action "start" failed.

```

---

### Post by bodhi.zazen on 2006-11-25
> **Bad Apple said:**
> done that, this is what it says. looks to me like it failed?!?! ...

No it installed just fine. It must be manually configured. You can read the README or 

usr/share/doc/915resolution/README.Debian then define
MODE, XRESO, and YRESO manually in /etc/default/915resolution or install 'vbetool'

I have never tried vbetool, but perhas that would help you:

```
sudo aptitude install vbetool
```

See [here](http://ubuntuforums.org/showthread.php?t=269052) for what I know about configuration of 915resolution.

---

### Post by Bad Apple on 2006-11-26
when I run the 915resolution -l it tells me

```

Unable to obtain the proper IO permissions: Operations not permitted

```
???

---

### Post by Bad Apple on 2006-11-26
okay, got into 915resolution to edit, and did so, but no joy still!!

when i try to run vbetool it gives me this

```

No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

```

---

### Post by bodhi.zazen on 2006-11-26
Can you post your xorg.conf

that is /etc/X11/xorg.conf

---

### Post by bodhi.zazen on 2006-11-26
[And here is yet another set of instructions for 915resolution](http://ubuntuguide.org/wiki/Dapper#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

---

### Post by Bad Apple on 2006-11-26
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
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
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
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
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by maddog39 on 2006-11-26
Well it looks as if to me that your X config is still using the old default driver. But I'M NOT SURE, so im just geussing lol. Someone else will have to confirm.

---

### Post by Bad Apple on 2006-11-27
how can i change that?

---

### Post by bodhi.zazen on 2006-11-27
> **Bad Apple said:**
> how can i change that?

Your driver is OK.

The problem is with your monitor section.

It currently looks like this> Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

As you may recall, I earlier advised you need to edit this (see post #3 of this thread and follow the link....). You need to add information on your monitor's horizontal and vertical refresh rates and add the "UseEdidFreqs" "1".

So it looks something like this:> 	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	29-121
	VertRefresh	50-180
        Option 		"UseEdidFreqs" "1"
EndSection

Only you will need to know your monitor's HorizSync and VertRefresh. Do not use my values. If you do not know them google search your monitor/laptop.

Alternately download an alternate live CD (Knoppix, Zenwalk Live) and get the settings from a xorg.conf that is working.

---

### Post by Bad Apple on 2006-11-27
at last, it works!! great stuff!! cheers for everyones help

---

### Post by bodhi.zazen on 2006-11-27
> **Bad Apple said:**
> at last, it works!! great stuff!! cheers for everyones help

At last indeed :p !

Congratulations, but I must admit I almost dreaded looking at this thread "one more time"! ;)

Also TY for updating us on your success....

Last.. Save a copy of that xorg.conf some where safe !

One last thing,

Welcome to Ubuntu (assuming you are new of course ;) )

---

