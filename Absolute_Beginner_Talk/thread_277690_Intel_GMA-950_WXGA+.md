---
title: "Intel GMA-950 WXGA+"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by sunami88 on 2006-10-15
Hey yall, iv been googling and searching the forums for about an hour or so, and still cant get my recently installed Ubuntu to display widescreen on my oh so sexy little Dell laptop.

I'm trying to run 1440x900_60, but no matter what i do, it displays 1024x768_60. Talk about ugly!

check out my xorg.conf;
```

Section "Device"
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	VideoRam	128000
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
	Modeline "1440x60_0.00" 154.20 1680 1712 2296 22328 1050 1071 1081 1103 -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth 32
		Modes		"1440x900"
	EndSubSection
EndSection

```


I'v tried dpkg-reconfigure xserver-xorg and 915resolution -l, and manual editing...

---

### Post by sunami88 on 2006-10-15
bump?

---

### Post by almahtar on 2006-10-20
The Intel drivers tend not to report widescreen resolutions, and that's what 915resolution is for.  It tells the driver to "replace" (temporarily) one of its resolutions with one of your choice.

To fix my widescreen agony, I did the following:

sudo 915resolution -l

This lists your video modes. Pick one to replace.

It gives me a big list of modes:

Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 945GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel

   .... lots of modes chopped out of the middle for brevity's sake ...

Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1680x1050, 32 bits/pixel

Mode 5c used to be some other resolution: I chose to replace it with the one I wanted.  So let's say I wanted to replace 5a instead:

sudo 915resolution 5c 1680 1050 32

So that's sudo 915resolution <mode you want to replace> <xresolution> <yresolution> <colordepth>

Assuming you've set up your xorg.conf correctly, you should be able to restart X and get glorious widescreen.

To make this happen every time you startup, put the 915resolution command in /etc/init.d/gdm right after the line that says:

log_begin_msg "Starting GNOME Display Manager..."

---

### Post by zman58 on 2006-11-26
Here is another suggestion which seemed to work out very well on my DELL D620:

I happen to be running MEPIS, which is based on UBUNTU, so I expect this information would be valid for UBUNTU as well.

The 915resolution deb package comes with a start script, named as you might expect "915resolution". If you have the 915resolution package installed in your system, then you should already have this script located at /etc/init.d/915resolution. You need to enable it for the runlevel you are operating in. Just add a symbolic link to /etc/init.d/915resolution for the proper runlevel which is runlevel 5 on my system. 

The symbolic link for run level 5 that I added to my system is S00resolution and looks like this...

cd /etc/rc5.d/
ls -l
[...]
lrwxrwxrwx 1 root root 23 2006-11-22 09:37 S00resolution -> ../init.d/915resolution
[...]

The 915resolution script uses the 915resolution default file located at:
/etc/default/915resolution

In this 915resolution default file on my system (DELL D620 w/Intel GMA 950) I have the following information:
#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=auto
#
# and set resolutions for the mode.
#
XRESO=1440
YRESO=900
#
# We can also set the pixel mode.
# Please note that this is optional,
# you can also leave this value blank.
BIT=24

I had to edit in the XRESO, YRESO, and BIT settings. The 1440x900 mode works great on my system.

As the man page for 915resolution states, you can find supporting information at:
/usr/share/doc/915resolution/README.Debian


The remainder of this post details how I got Open GL working...

Furthermore, To get Open GL working on this DELL D620, I found out that I had to add a "VideoRam 128000" setting into /etc/X11/xorg.conf like so:

[...]
Section "Device"
  Identifier  "Card0"
  Driver "i810"
  BoardName "unknown"
  VideoRam 128000
[...]

It seemed that the system needed to be completely cold-started once these changes were made. Perhaps by repetetivly restarting X, I may have confused the chipset trying multiple other VideoRam value settings before doing a man i810 and reading that the i810 can manage only up to 128MB of VideoRam.

Video support seems to be working now; That is to say, I have Open GL support at 1440x900 with the Intel GMA 950 video chip.
:)

---

