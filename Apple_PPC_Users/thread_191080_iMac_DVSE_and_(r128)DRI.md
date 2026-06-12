---
title: "iMac DVSE and (r128)DRI"
date: 2006-06-07
forum: Apple PPC Users
---

### Post by philip987 on 2006-06-07
I updated to dapper from breezy a few days ago with little joy as X fell over and I could not be bothered trying to diagnose it so I did a fresh install from sratch.
I have been using Ubuntu since Warty warthog and 'apt-get upgrade' has only ever been fully succesful once in my limited experience and as a command line fills me with fear and trepidation, so I was prepared for this with needed backups.

Everything seems to be fine except I can't get dri enabled.  I never did manage to get it going in any previous version so I have little idea what to do. I have tried changing the default depth to 16 bit but this just crashes X again.
Other than this minor problem, the rest of dapper looks and feels a big step forward. Well done

---

### Post by Sav on 2006-06-07
I did a fresh install of xubuntu dapper on my imac g3 500 dv, and I was unable to tweak the xorg.conf file to get any accelleration.
Infact, changing the default depth to 16 bit (as it's explained) only makes the windows system to load extremely slow.
The rest is perfect: much more faster then tiger.

---

### Post by daft_ska on 2006-06-17
I have the answer to this caevet.
I too could not for the life of me get DRI going on my iMac G3 500, but this guy named Conn at launchpad seems to have the answer.

[https://launchpad.net/distros/ubuntu/+source/mesa/+bug/24810](https://launchpad.net/distros/ubuntu/+source/mesa/+bug/24810)

go into the responses/comments and download the r128_cceidle.diff file and follow his instructions.
Using "glxgears -printfps" I went from 30 FPS to 300 FPS, and now am quite happy with my rendering capabilities.  Still too slow for awesome penguin racing, but it does work now.

---

### Post by linear on 2006-06-18
[quote=daft_ska]I have the answer to this caevet.
I too could not for the life of me get DRI going on my iMac G3 500, but this guy named Conn at launchpad seems to have the answer.

[https://launchpad.net/distros/ubuntu/+source/mesa/+bug/24810]("https://launchpad.net/distros/ubuntu/+source/mesa/+bug/24810")

go into the responses/comments and download the r128_cceidle.diff file and follow his instructions.
[/quote] I may be missing something, or perhaps the instructions expect more knowledge...

The first three steps are as follows:

 sudo apt-get build-dep xserver-xorg-driver-ati
 sudo apt-get source xserver-xorg-driver-ati
 cd xserver-xorg-driver-ati-x.x.x.x/src (replace the x's with Breezy's version)

Steps 1 and 2 are OK, or so it seems. I'm stumped at step 3, as the directory described isn't there. There's no "xserver-xorg-driver-ati-<version>" directory that I can find. There's an "xorg-6.8.2" directory, but no "src" directory under it. Where do I go from here?

---

### Post by daft_ska on 2006-06-19
In my case, "ls" gave me these results:
"jake@jake-desktop:~$ ls
Desktop
Doom.wad
Examples
ID1
r128_cceidle.diff
xserver-xorg-driver-ati-6.5.7.3
xserver-xorg-driver-ati_6.5.7.3-0ubuntu7.diff.gz
xserver-xorg-driver-ati_6.5.7.3-0ubuntu7.dsc
xserver-xorg-driver-ati_6.5.7.3-0ubuntu7_powerpc.changes
xserver-xorg-driver-ati_6.5.7.3-0ubuntu7_powerpc.deb
xserver-xorg-driver-ati_6.5.7.3.orig.tar.gz"

so, in my case, the proper command was:

cd xserver-xorg-driver-ati-6.5.7.3/src

hope that helps!

---

### Post by linear on 2006-06-19
After looking into it some more...
 
The problem, I think, is that I've been sitting on the fence and have not yet upgraded to Dapper. The "xserver-xorg-driver-ati" sources as described currently exist in the Dapper and Edgy repos only. Why **apt-get source** returns something else from the Breezy repo is a bit of a mystery.

---

### Post by Sav on 2006-06-20
[QUOTE=linear]After looking into it some more...
 
The problem, I think, is that I've been sitting on the fence and have not yet upgraded to Dapper. The "xserver-xorg-driver-ati" sources as described currently exist in the Dapper and Edgy repos only. Why **apt-get source** returns something else from the Breezy repo is a bit of a mystery.[/QUOTE]

I gave up on ati.
I installed xubuntu 6.06 on my iMac g3 500 dv and on an old acer laptop.
Both the computers have an ati chip inside: the r128 in the iMac, the mach64 in the laptop.
By the way, the direct rendering doesn't work on any of both, no matter I tried to compile the dri drivers directly from the sources, as explained in many tutorials.

I admit that the mach64 chipset is very old, so I'm happy just seeing the X interface.
But the r128 is already something whorty.

---

### Post by ZoiaGuyver on 2007-03-19
Sorry if this is a little late :D

I had this problem on my G3 iMac 600 with a Rage 128 Pro Ultra TR. It seems to be a problem with the agpgart as reported in many bugposts. Heres how you can get DRI and GLX working (even AIGLX)

First off get to a prompt (ctrl-alt-F1)

at the prompt type 

sudo nano /etc/X11/xorg.conf

look for the modules section in there insert a # before all but

load "dri"
load "dbe"
load "extmod"
load "freetype"
load "glx"

Then find the section about the graphics card in there type

Option "useFBdev" "false"
Option "SWCursor" "true"
Option "ForcePCIMode" "true"

That should get you a working DRI and GLX. 

Heres my Xorg.conf 

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
#	Load	"i2c"
#	Load	"bitmap"
#	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"dbe"
	Load	"glx"
#	Load	"int10"
#	Load	"type1"
#	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"ATI Technologies, Inc. Rage 128 Pro Ultra TR"
	Driver		"ati"
	Option		"UseFBDev"		"false"
	Option		"SWcursor"		"true"
	Option		"ForcePCIMode"		"true"
	Option  "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	58-62
	VertRefresh	75-117
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage 128 Pro Ultra TR"
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
	Option         "AIGLX" "true"
EndSection

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection


Hope this helps someone.


Ahhh forgot to say this is working on 2 identical G3 600 iMacs in 6.10 edgy eft

---

### Post by linear on 2007-03-21
> **ZoiaGuyver said:**
> Heres how you can get DRI and GLX working (even AIGLX)

First off get to a prompt (ctrl-alt-F1)

at the prompt type 

sudo nano /etc/X11/xorg.conf

look for the modules section in there insert a # before all but

load "dri"
load "dbe"
load "extmod"
load "freetype"
load "glx"

Then find the section about the graphics card in there type

Option "useFBdev" "false"
Option "SWCursor" "true"
Option "ForcePCIMode" "true"

That should get you a working DRI and GLX.

Hats off to ZoiaGuyver! This works for Dapper too (iMac G3 500 MHz slotloading).

---

### Post by ZoiaGuyver on 2007-03-22
glad it could help :D

---

### Post by CrystalBaller09 on 2007-05-14
> **ZoiaGuyver said:**
> Sorry if this is a little late :D

I had this problem on my G3 iMac 600 with a Rage 128 Pro Ultra TR. It seems to be a problem with the agpgart as reported in many bugposts. Heres how you can get DRI and GLX working (even AIGLX)

First off get to a prompt (ctrl-alt-F1)

at the prompt type 

sudo nano /etc/X11/xorg.conf

look for the modules section in there insert a # before all but

load "dri"
load "dbe"
load "extmod"
load "freetype"
load "glx"

Then find the section about the graphics card in there type

Option "useFBdev" "false"
Option "SWCursor" "true"
Option "ForcePCIMode" "true"

That should get you a working DRI and GLX. 

Heres my Xorg.conf 




Hope this helps someone.


Ahhh forgot to say this is working on 2 identical G3 600 iMacs in 6.10 edgy eft

I tried this but when i run:
```
glxinfo | grep rendering
```
i still get no direct rendering

If it helps, my graphics card is an "ATI 3D Rage Pro 215GP (rev 5c)" according to lspci.

---

