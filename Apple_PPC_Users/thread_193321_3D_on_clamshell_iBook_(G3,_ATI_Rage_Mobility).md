---
title: "3D on clamshell iBook (G3, ATI Rage Mobility)?"
date: 2006-06-09
forum: Apple PPC Users
---

### Post by vyruss on 2006-06-09
Hi everyone!

I've gotten Dapper to run on a G3 original iBook (tangerine clamshell) with a G3 processor, 128MB RAM and an ATI Rage Mobility L AGP 2x video board. This belongs to the Mach64 line of ATI cards and while the Mach64 modules are finally included and are being loaded, DRI (3D acceleration) doesn't work.

I know DRI won't be impressive, but every little bit helps on such an old machine. Has anyone managed to make it work?

Thanks,
Jimmy

---

### Post by steward75 on 2006-06-09
How did you get it installed?  I have the same iBook, but mine keeps freezing before even switching over to the Kernel. Did you use the live CD and install from that or did you use the alternate install cd?

---

### Post by vyruss on 2006-06-09
[QUOTE=steward75]How did you get it installed?  I have the same iBook, but mine keeps freezing before even switching over to the Kernel. Did you use the live CD and install from that or did you use the alternate install cd?[/QUOTE]

It has so little RAM it definitely needs a swap partition. What I did is a bit crazy, but it worked. I booted the Xubuntu live CD, auto-partitioned the drive (which also created a swap partition), then aborted the installation and booted the normal Ubuntu live CD and just clicked on the installer on the desktop.

It's slow as hell, but worth it.


EDIT: Do you have enough RAM? 128MB works for the above procedure. Also, make sure you have a properly burned (or pressed) copy of the Ubuntu CD. The CDROM on the iBook is a bit picky when booting, so burn your copy reliably (i.e. at a slow speed).

---

### Post by steward75 on 2006-06-10
Huh,  cause everytime I try to boot the live CD, it gives the error message about not being allocate some sort of device tree something or other before it even loads up the kernel for hte live CD so that's why I'm a little surprised, unless they maybe updated the live CD isos already with the new kernel....

---

### Post by steward75 on 2006-06-10
I'm sorry I forgot to mention that once it gives me that error message, it kicks me back to the Openfirmware prompt.

---

### Post by AlphaMack on 2006-06-10
Yup, it dumps you to OF and won't let you boot.

---

### Post by vyruss on 2006-06-10
[QUOTE=steward75]Huh,  cause everytime I try to boot the live CD, it gives the error message about not being allocate some sort of device tree something or other before it even loads up the kernel for hte live CD so that's why I'm a little surprised, unless they maybe updated the live CD isos already with the new kernel....[/QUOTE]

I have no idea what's wrong. Are you sure you have at least 128 mb ram and the live CD is burned properly? Also, I booted using the latest (final) 6.06 CDs.

---

### Post by nkbj on 2006-06-11
[QUOTE=steward75]I'm sorry I forgot to mention that once it gives me that error message, it kicks me back to the Openfirmware prompt.[/QUOTE]
You've been bitten by this bug: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508)

Regards,
Niels Kristian

---

### Post by steward75 on 2006-06-11
Vyruss, I'm good on the memory and running the latest version of the live cd but for whatever reason I'm bit by this bug and why you aren't affect I do not know. :-(  Looks like I'll have to wait until they update the kernel for the liveCD for it to install.

Steward75

---

### Post by vyruss on 2006-06-11
[QUOTE=steward75]Vyruss, I'm good on the memory and running the latest version of the live cd but for whatever reason I'm bit by this bug and why you aren't affect I do not know. :-(  Looks like I'll have to wait until they update the kernel for the liveCD for it to install.

Steward75[/QUOTE]

Very strange. I posted this on the bug report: "*June 7th's Xubuntu and Ubuntu desktop CDs do not exhibit this bug on a G3 300 MHz tangerine clamshell iBook with 128 MB RAM.*" I'm sorry I can't help more, good luck!

---

### Post by nkbj on 2006-06-11
The bug seems to depend on the actual memory configuration.

vyruss: Is your 128MB RAM in one DIMM or two?

---

### Post by LingXioayu on 2006-06-13
I bet youve never upgraded the firmware have you? I have a sneaking idea thats what does it. I have the exact same Ibook and it does it. If I had the orginal ibook firmware and was able to downgrade it I bet 6.06 would work fine. Cause I have 288megs of ram and a 1gig swap disk and it still dumps on me.

---

### Post by nkbj on 2006-06-14
The bug seems to occur only on systems with two DIMM's of different sizes. I suspect that vyruss has 2*64MB RAM and that is why it work on his system.

---

### Post by vyruss on 2006-06-14
OK, I checked by phone because the iBook is no longer in my hands:

It has 64MB onboard RAM and a 64MB DIMM installed, also the firmware has been upgraded from Apple.

---

### Post by steward75 on 2006-06-24
Well just thought I would give you all an update.  I decided that if I couldn't have 6.06 I would just live with 5.10 until the bug could be fixed.  So after, oh, 30 some odd times of trying to install 5.10 ( I think my CD-Rom drive is failing) I was EVENTUALLY able to get it installed.  After that it notified me that a new version of Ubuntu was avail for install once I finally booted into the desktop but I chose not to and just update the packages for 5.10.  Yeah the curiousity lasted me 3 days before I gave in and decided to update through Update Manager.  It downloaded the files it needed, updated the files, rebooted and........

IT WORKED!   I booted in just fine to 6.06 and it's been working great so far.  Glad to be back to Ubuntu from Fedora 4 core.

**by the way, my memory configuration is 32 megs onboard then a 128 meg addon. (and I do believe, it's been a while, but I think when I upgraded from OS 9 to OS X 10.3.?  it upgraded the firmware on my mac)

---

### Post by bigfox on 2006-06-24
My iBook also dropps to the Open Firmware prompt.

Blue iBook 300Mhz G3 288 MB RAM (32 onboard + 256 upgrade)

I think its just its old CD drive.

---

### Post by Kelvin on 2006-07-10
Hello All!

Anyone have a thought on the original question of getting 3D to work? Why does it work on some, but not others.

I have a graphite iBook SE, 366mHz clamshell, 312MB of ram, running xubuntu.

Running glxinfo tells me

direct rendering: No

Is this a matter of installing a missing package or running a config somewhere?

Any help is appreciated. :D 

Kelvin

---

### Post by daft_ska on 2006-07-11
I'm currently between classes, but I struggled with this too and mangaed to get DRI going on my iMac with the ATI Rage 128...8)  I orginally thought it was due to this patch that I made, but it helped to add some modules to /etc/modules and add some option lines to xorg.conf.  I'll post my /etc/modules and xorg.conf as well as a link to the patch I used, to give everyone a fighting chance at ending up where I did.  I'm now getting 300-400 fps in glxgears, where it used to be ~30.  Good times.  If you want to get a jump start on that patch, you may wish to look for other posts I made.

---

### Post by daft_ska on 2006-07-20
first, make sure r128 and agpgart are added to /etc/modules
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

r128
agpgart
uninorth_agp
genrtc
snd_powermac
apm_emu
sbp2
snd-powermac
sr_mod

```
and make sure you have the AGP parts in your xorg.conf like this:
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
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"v4l"
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
	Identifier	"ATI Technologies, Inc. Rage 128 Pro Ultra TR"
	Driver		"r128"
	BusID		"PCI:0:16:0"
	VideoRam	16000
	Option		"CCEusecTimeOut"	"20000"
	Option		"AGPMode"		"4"
	Option		"AGPSize"		"32"
	Option		"EnablePageFlip"	"true"
#	Option		"Display"		"BIOS"
	Option		"SWCursor"		"true"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"iMac"
	Option		"DPMS"
	HorizSync	60-60
	VertRefresh	75-117
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage 128 Pro Ultra TR"
	Monitor		"iMac"
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

```

if that doesn't help, let me know.

---

### Post by Gen2ly on 2006-12-02
This is an iMac hack, don't try it on clamshell iBooks.  Uh, yes I did try it and had to learn vi realy quick.  I haven't heard anything about getting video acceleration going (heck, I don't even know how to check it.)  I'm running 6.10 and the video seems alright.

As for the problems starting with a CD here is the [iBook Open Firmware updates]("http://download.info.apple.com/Apple_Support_Area/Apple_Software_Updates/English-North_American/Macintosh/iBook/").  This is definitely recommended, I didn't have any problems with the CD drive.  My only problem is the Ubuntu installatoin has made my MacOS boot null.

---

### Post by dpny on 2006-12-05
In order to get direct rendering, you need to edit xorg.conf to make the default monitor/display depth 16, or what OS X would call "Thousands of colors". 24 bit just takes more VRAM than the chip has. It makes things a little better on my Pismo.

---

### Post by ik79 on 2007-01-07
could you send me a link or tell me how to start 3D acceleration on my Mac iBook g3? it runs mac os x 10.3.9, please, please, please, please, help me please! I have tried to play WoW (or world of warcraft) the video driver is ATI RAGE MOBILITY L (or 128 I think) please send me a link or tell me how to enable 3D acceleration! (mac classic does not work on it)

---

### Post by dpny on 2007-01-07
> **ik79 said:**
> could you send me a link or tell me how to start 3D acceleration on my Mac iBook g3? it runs mac os x 10.3.9, please, please, please, please, help me please! I have tried to play WoW (or world of warcraft) the video driver is ATI RAGE MOBILITY L (or 128 I think) please send me a link or tell me how to enable 3D acceleration! (mac classic does not work on it)

If you're running OS X, then you have all the acceleration you'll ever get.

---

### Post by ik79 on 2007-01-13
ok, I have tried what you requested, but the application still won't work, if I haven't already posted the application name it is World Of Warcraft that doesn't run unless 3D acceleration works and I have no clue as how to enable it.

---

