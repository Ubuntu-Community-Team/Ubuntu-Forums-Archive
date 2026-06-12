---
title: "PowerPC G4 Cube - ATI Rage 128 Video Driver &quot;r128&quot; - Need help configuring"
date: 2008-11-07
forum: Apple Hardware Users
---

### Post by hos on 2008-11-07
Hello Forum ...

Recently, I tackled installing Ubuntu 8.04 Hardy on a PowerPC G4 Cube. The installer configured xorg.conf with the video driver "r128" which led to the GUI not loading and dropped to a command prompt. Once I edited the xorg.conf device section to use the "fbdev" driver, I was able to finally boot into the GUI desktop of Ubuntu Gnome.

Unfortunately, the display depth of "fbdev" defaults to 8 and any changes to the DefaultColorDepth in xorg.conf causes the GUI not to load. The results are a very griny looking desktop.

It appears that the driver "r128" loads properly and finds the ATI Rage 128 Pro board and chipset without problem. You can see in the Xorg.log that the trouble comes when the submodule framebuffer "fbdevhw" tries to load and fails ... it cannot find the directory/files it is looking for. so it unloads and falls back to a command prompt.

_xorg.conf_

Section "InputDevice"
	Identifier	"Apple Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:lwin_switch"
EndSection

Section "InputDevice"
	Identifier	"Kensington Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"ATI Rage"
	BoardName	"ATI Rage 128 PF/PRO AGP 4X"
	BusID		"PCI:0:16:0"
	Driver		"r128"
EndSection

Section "Monitor"
	Identifier	"Apple LCD"
	VendorName	"Apple"
	ModelName	"Studio Display"
EndSection

Section "Screen"
	Identifier	"Screen 1"
	Monitor		"Apple LCD"
	Device		"ATI Rage"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen 1"
EndSection

_Xorg.0.log_

(II) Setting vga for screen 0.
(II) R128(0): PCI bus 0 card 16 func 0
(II) R128(0): Creating default Display subsection in Screen section
	"Screen 1" for depth/fbbpp 24/32
(==) R128(0): Depth 24, (==) framebuffer bpp 32
(II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) R128(0): Default visual is TrueColor
(II) R128(0): VGAAccess option set to FALSE, VGA module load skipped
(==) R128(0): RGB weight 888
(II) R128(0): Using 8 bits per RGB (8 bit DAC)
(**) R128(0): Using framebuffer device
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.0.2
	ABI class: X.Org Video Driver, version 2.0
(WW) open /dev/fb1: No such file or directory
(WW) open /dev/fb2: No such file or directory
(WW) open /dev/fb3: No such file or directory
(WW) open /dev/fb4: No such file or directory
(WW) open /dev/fb5: No such file or directory
(WW) open /dev/fb6: No such file or directory
(WW) open /dev/fb7: No such file or directory
(EE) Unable to find a valid framebuffer device
(EE) R128(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
	(you may have to look at the server log to see warnings)
(II) UnloadModule: "r128"
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
(EE) Screen(s) found, but none have a usable configuration.

I have searched throughout the forum and other website resources and have tried all configurations I found for xorg.conf using the "r128"... all without any success. It appears that there has been a recent modification to the ATI driver set but only for X86. 

* Has anyone had success with "r128" driver and the ATI Rage 128 Pro card on a powerpc (an older driver perhaps)? 

* Has anyone a working xorg.conf file for the powerpc and this card?

* Or, has anyone been able to change the color depth of the "fbdev" driver for use with the ATI card?

Hopefuly, someone out there has conquered this issue and a resolution is a hand.

Thanks in advance for all the help!

---

### Post by stream303 on 2008-11-09
Be sure to visit the PPC archive read-only forum. There are a few references to Cubes, perhaps this one will get you started:

[http://ubuntuforums.org/showthread.php?t=772808](http://ubuntuforums.org/showthread.php?t=772808)

Note that depending on what video monitor you are using, you may have to alter your video frequencies from what is shown in the thread.

---

### Post by hos on 2008-11-09
Thanks for the direction stream303 ... 

I actually had already checked that thread out (and many others) and to date have found no success.

My belief now is that the "r128" driver for the powerpc may be in need of an update and is not compatible with Hardy 8.04 ... for whatever reason, it appears to call on the framebuffer "fbdevhw" and when it tries to load it, it fails as it can't find the called on files/directories.

What's interesting is that the "fbdev" generic video driver has no problem loading the framebuffer.

I may submit this as a "bug" and see if I can reach a solution that way!

Thanks again!

---

### Post by ginbas on 2008-11-16
I am also having similar issue with G3 and pci rage 128.

---

### Post by IQRules on 2008-11-16
> **hos said:**
> Thanks for the direction stream303 ... 

I actually had already checked that thread out (and many others) and to date have found no success.

My belief now is that the "r128" driver for the powerpc may be in need of an update and is not compatible with Hardy 8.04 ... for whatever reason, it appears to call on the framebuffer "fbdevhw" and when it tries to load it, it fails as it can't find the called on files/directories.

What's interesting is that the "fbdev" generic video driver has no problem loading the framebuffer.

I may submit this as a "bug" and see if I can reach a solution that way!

Thanks again!

Try this to make sure if video driver r128 is issue here.
Enter rescue mode, mount the / partiton from hard drive.
You might want chroot /target first. You can vi or nano on xorg.conf, then run startx.

I went this far couple day ago and X is up and running.

---

### Post by Kuroyi on 2008-11-17
I have this same problem on my G3 12" iBook2. It just started after I upgraded from 8.04 to 8.10.

With UseFBDev "true" I get the device not found error, and with UseFBDev "false" I get problems with the Int10 driver. I was able to resolve it for now by using Driver "fbdev" instead of letting X use r128 (I also commented out dri, glx, and int10 for good measure).

Now I'm hitting some glitches due to running on a G3 machine. I recompiled libpixmap without altivec and that fixes some of my issues, but my drive icons on the left won't launch anything. Well, they start and then disappear. I'm fairly new to Ubuntu (Xubuntu) so I'm not sure what that application is called.

---

### Post by khelben1979 on 2008-11-18
> **ginbas said:**
> I am also having similar issue with G3 and pci rage 128.

I'm very interested to know if and how I can fix this myself. I have an old Powerbook G3 "Lombard" where I'm not certain if it uses the full potential of the inbuilt ATi Rage chip.

I suspect that the hardware acceleration isn't active in my case, although I am able to watch movies if it's in a very, very low video quality.

At first I thought that it might had to do with my old computer, but it's not that old, and I remember having much more speed in the graphics when I used to run Debian Woody on it together with the Xfree86 server.

I haven't felt that I've wanted to change back to the XFree86 x-server either because I want to follow Debian standard in this regard, and if they choose X.org in favour over XFree86 I will go for this instead, which I've done.

---

### Post by skigil on 2008-11-27
> **hos said:**
> Thanks for the direction stream303 ... 

I actually had already checked that thread out (and many others) and to date have found no success.

My belief now is that the "r128" driver for the powerpc may be in need of an update and is not compatible with Hardy 8.04 ... for whatever reason, it appears to call on the framebuffer "fbdevhw" and when it tries to load it, it fails as it can't find the called on files/directories.

What's interesting is that the "fbdev" generic video driver has no problem loading the framebuffer.

I may submit this as a "bug" and see if I can reach a solution that way!

Thanks again!

I'm having the same issues.  How do you load it up with fbdev, rather than fbdevhw?

---

### Post by stream303 on 2008-11-28
Cube and G3 r128 possibilities?

Part of the problem with cube may be that you might want to specify your vertical and horizontal freqs particular to that monitor, an possibly force a resolution mode as well as your custom r128 options

Here's an old cube thread with xorg.conf, but I don't think he's using a nice Cinema display..

[http://ubuntuforums.org/showthread.php?t=772808](http://ubuntuforums.org/showthread.php?t=772808)

As for the G3 iMacs, here is a nice one where the user was able to even get dri and glx working with an r128:

[http://ubuntuforums.org/showpost.php?p=2321892&postcount=8](http://ubuntuforums.org/showpost.php?p=2321892&postcount=8)

Some of the older xorg stuff may no longer be necessary like the files section, or the input device section, but I see some interesting values that might be just the ticket for a custom xorg.conf with hardy / intrepid.

Thought I'd toss that out - wish I had access to either one of these machines so I could dig in...

---

### Post by greenergardening on 2008-12-29
Hello,

Im have a similair problem with my compaq presario 1800t. I recently installed the newest version of xubuntu, everything was going smoothly until i restarted and received a message after booting. It said it was running in low graphics mode errors: unable to find valid frame buffer device and r 128 (0) failed to open Framebuffer device. I've been reading these forums and trying different possibilities, but to no avail. 

This is the xorg.conf.new doc i saved.
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "xtrap"
	Load  "dri"
	Load  "record"
	Load  "extmod"
	Load  "glx"
	Load  "dbe"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "Dac8Bit"            	# [<bool>]
        #Option     "DMAForXv"           	# [<bool>]
        #Option     "ForcePCIMode"       	# [<bool>]
        #Option     "CCEPIOMode"         	# [<bool>]
        #Option     "CCENoSecurity"      	# [<bool>]
        #Option     "CCEusecTimeout"     	# <i>
        #Option     "AGPMode"            	# <i>
        #Option     "AGPSize"            	# <i>
        #Option     "RingSize"           	# <i>
        #Option     "BufferSize"         	# <i>
        #Option     "EnablePageFlip"     	# [<bool>]
        #Option     "Display"            	# <str>
        #Option     "PanelWidth"         	# <i>
        #Option     "PanelHeight"        	# <i>
        #Option     "ProgramFPRegs"      	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "VideoKey"           	# <i>
        #Option     "ShowCache"          	# [<bool>]
        #Option     "VGAAccess"          	# [<bool>]
	Identifier  "Card0"
	Driver      "r128"
	VendorName  "ATI Technologies Inc"
	BoardName   "Rage Mobility M3 AGP 2x"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection





 Can anyone give me a pointer or two? im a novice to linux, but am eager to learn the tricks.

Thanks for your help :)

---

### Post by Manfred123 on 2008-12-29
I like the idea, cool!

---

### Post by bitglue on 2009-01-07
Try adding in the Device section:

Option "UseFBDev" "false"
Option "NoInt10" "true"

Also to make things work on my cube I had to tell it I actually did want a keyboard and mouse:

Section "InputDevice"
Identifier "Generic Mouse"
Driver "mouse"
Option "CorePointer"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
EndSection

---

### Post by dmcglynn on 2009-03-28
> **bitglue said:**
> Try adding in the Device section:

Option "UseFBDev" "false"
Option "NoInt10" "true"



THANK you for posting about the "NoInt10" option. I had seen in my logs where it was crashing just after loading the Int10 driver, but didn't know that this option existed.

My X is working thanks to you!

---

### Post by mameisam on 2009-07-17
Has anyone figured out how to fix the 8-bit depth issue for the fbdev driver or managed to use r128 driver on G4 Cube? Thanks

---

### Post by narcisgarcia on 2011-11-25
With an iMac G3 350 (ATI), all the examples of xorg.conf worked for me when I added the following line in the "Device" section:
```
Option "NoInt10" "true"
```
(Ubuntu 11.04)

Colaborative wiki for Apple iMac G3 and others:
[http://wiki.lapipaplena.org/index.php/AppleImacG3350-ubuntu1104](http://wiki.lapipaplena.org/index.php/AppleImacG3350-ubuntu1104)

---

