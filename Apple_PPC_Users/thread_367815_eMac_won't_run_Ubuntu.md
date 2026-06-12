---
title: "eMac won't run Ubuntu"
date: 2007-02-22
forum: Apple PPC Users
---

### Post by Shack_ on 2007-02-22
Sorry this is so long, but...

I booted an eMac from the PowerPC installation CD for Ubuntu 6.10. A message came up prompting me for a kernel to load. I selected the default kernel (live) and ubuntu started to boot.

However, a message came up that said:

Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

There were two options: <Yes> and <No>
I used the keys to hit <Yes> and the following message was displayed:

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build OS: Lin 2.6.17-9-powerpc64-smp ppc
Current OS: Lin ubuntu 2.6.17-10 powerpc #2 Fri Oct 13
16:37:41 UTC 2006 ppc
Build Date: 07 Jully 2006
          Before reporting problems, check [http://wiki.org](http://wiki.org) to make sure you have the latest version.
Module Loader Present
Markers: (--) probed, (**) from config file, (==) default setting,
              (++) from command line, (!!) notice (II) informational,
              (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Feb 21 20:14:41 2007
(==) Using config file: "/etc/X11/xorg.conf"
(WW) ****INVALID IO ALLOCATION**** b: 0xF0000400 c: 0xF00004ff
correcting^G
(EE) end of block range 0xefffffff < begin 0xf0000000
(**) RADEON(0): RADEONPreInit
(EE) RADEON(0): MergedFB does not work with Option UseFBDev, MergedFB mode is disabled
(**) RADEON(0): RADEONScreenInit 98000000 0
(**) RADEON(0): RADEONSave
(**) RADEON(0): DRI New memory map param
(**) RADEON(0): RADEONInitMemoryMap() :
(**) RADEON(0):    mem_size                 : 0x04000000
(**) RADEON(0):   MC_FB_LOCATION      :0x7fff0000
(**) RADEON(0):  MC_AGP_LOCATION    :0xffffffc0
(EE) RADEON(0): FBIOPUT_VSCREENINFO: Invalid argument

Fatal server error:
AddScreen/ScreenInit failed for driver 0

(**) RADEON(0): RADEONLeaveVT
   (**) RADEON(0) RADEONRestore
(**) RADEON(0): Ok, leaving now...


I hit okay, then another message showed up that read:

Would you like to view the detailed X server output as well?
<Yes> <No>

When I hit yes the text was ridiculously long, so I can't put it here.

Another message showed:
The X server is now disabled. Restart GDM when it is configured correctly.
<Ok>

The screen went black with a blnking cursor and didn't do anything else. I had to turn off the computer.

I apologize for the length of this post, and would seriously appreciate help.

---

### Post by rccharles on 2007-02-22
Try this article:

[http://www.linux.com/article.pl?sid=06/10/24/1817237](http://www.linux.com/article.pl?sid=06/10/24/1817237)

Robert

---

### Post by deleted1028 on 2007-02-24
when I first used Ubuntu x failed everytime. I Use an emac 1ghz with the radeon card and what fixed it for me was in /etc/X11/xorg.conf  changing the default settings to this under the monitor section
	HorizSync    71.0 - 73.0
	VertRefresh  70.0 - 140.0
        Option       "UseFBDev"
        Modeline     "1280x960" 122.25 1280 1328 1424 1696 960 961 964 1002 +hsync +vsync -csync
        Option       "DPMS" 


then further down in the screen section changing the default to 

SubSection "Display"
		Depth	1
		Modes "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes "1280X960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	32
		Modes "1280x960" "1024x768" "800x600" "640x480"


-hope this helps ,..Scott

---

### Post by Auria on 2007-02-24
I am on eMac

this is how i solved it:

when on a terminal:

sudo bash
dpkg-reconfigure xserver-xorg

i accepted all defaults except monitor - i changed "iMac" to "eMac"

then accept all other following defaults (if it defaults to 8 or 16 bits maybe select 24 bits)

then

sudo killall -HUP gdm

and it worked!
hope it helps

---

