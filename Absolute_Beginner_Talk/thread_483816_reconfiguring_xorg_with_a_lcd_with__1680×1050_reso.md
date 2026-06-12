---
title: "reconfiguring xorg with a lcd with  1680×1050 resolution"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by ltk5 on 2007-06-25
I'm trying tor econfigure xserver or xorg (don't knowthe difference) by following a How To found here on ubuntuforums.
When I test my settings all i get is a small (about 5x5cm) window, which looks like a terminal. There are no borders, and my cursor turns into a big X outside this terminal.

The first problem is, that I'm not sure if i selected the correct graphic card. I'm using an intel core duo and I selected a i810 chipset, before that I selected vesa, and the results were the same.

The monitor I'm trying to set up is a SonicView 22''.

---

### Post by FurryNemesis on 2007-06-25
Could you please post your current xorg.conf file? It would help us help you if we could see what was going on.

---

### Post by cwmoser on 2007-06-25
I use two 21" Sceptre monitors in 1680x1050 mode with an nVidia video card.

Here is how I configured my /etc/X11/xorg.conf file - perhaps you can get a hint from it.
The "twinview" option enables the dual monitor effect.

Carl


Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"

    #Driver         "nv"
    #Driver         "nvidia"
    Identifier     "nVidia Corporation NV44A [GeForce 6200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV44A [GeForce 6200]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "twinview"
    Option         "TripleBuffer" "true"
    Option         "AllowGLXWithComposite" "True"
    Option         "RenderAccel" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by ltk5 on 2007-06-25
bellow is attached  my xorg.conf.
I'll compare your settings cwmoser with mine. thx

---

### Post by BlackMeTaL on 2007-06-25
Can you post the output of the command xrandr?

---

### Post by ltk5 on 2007-06-25
it says: can't open display

---

### Post by ltk5 on 2007-06-25
Ok. I rebooted my machine, ran xrandr again. this is what I get.
```
lotko@lotko-desktop:~$ xrandr
 SZ:    Pixels          Physical       Refresh
*0    640 x 480    ( 217mm x 163mm )  *60  
Current rotation - normal
Current reflection - none
Rotations possible - normal 
Reflections possible - none

```
any suggestion would be helpfull.

---

### Post by BlackMeTaL on 2007-06-25
I'm pretty sure it's your videocard.

Chech this info:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

---

### Post by coffeecat on 2007-06-25
You need to include the correct video driver in the Device section of xorg.conf as well as put the 1680x1050 resolution in the Display section the way cwmoser has done it.

The i810 driver is for the Intel graphics chipset but some older Intel graphics chipsets won't support 1680x1050. The Intel core duo is the cpu - it doesn't necessarily mean you have an Intel graphics chipset. The vesa driver is a generic one and limited - as far as I remember it won't do anything greater than 1280x1024.

You need to be sure what graphics chipset you have. Open a terminal and do the command:

```
lspci
```Somewhere among that output will be details of the graphics card. In mine the line starts 'VGA compatible controller'. Post that line and we can see what video card you have and someone can advise what driver to put in the Device section. The nv and nvidia drivers that are referred to in cwmoser's xorg.conf are the open-source and proprietary drivers respectively for nvidia cards.

---

### Post by ltk5 on 2007-06-25
```
lotko@lotko-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82946GZ/PL/GL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82946GZ/GL Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
04:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)

```

---

### Post by coffeecat on 2007-06-25
This is it:

```
00:02.0 VGA compatible controller: Intel Corporation 82946GZ/GL Integrated Graphics Controller (rev 02)
```Yes, the i810 driver is the one you need. However, one of my machines has the Intel 82845G chipset and I can't get more than 1280x1024 resolution with it when it's connected to my 1680x1050 monitor. But I doubt that's the cause of what you describe in your first post.

Have you ever had a decent display with that monitor? Which was the howto you were following?

---

### Post by ltk5 on 2007-06-25
I was using [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

When I was using my LG 15''  everything went fine, of course at that time I only needed 1024x768.

---

### Post by cwmoser on 2007-06-25
From reading your xorg.conf file, I noted you have a tablet PC and the video is i810 -- sounds similar to mine.  I have a Gateway Tablet Notebook.

Well, below is the /etc/X11/xorg.conf file I use with my Gateway Tablet Notebook and it works perfectly with Beryl at 1280x768 resolution.

Carl

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Load	"vbe"
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
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
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by ltk5 on 2007-06-27
Ok, I think I've found a solution. As i did some more search i found this topic: [http://ubuntuforums.org/showthread.php?t=290503](http://ubuntuforums.org/showthread.php?t=290503)

and in the reply #8 ([http://ubuntuforums.org/showpost.php?p=2871538&postcount=8](http://ubuntuforums.org/showpost.php?p=2871538&postcount=8)), Gremlinzzz writes about installing intel drivers instead of i810. I don't know if only the new drivers helped, or was it the combination with 915resolution.

I did a ctrl+alt+backspace and the resolution is nice, I even have some options to change it to lower or higher.
I just wonder what'll happen when I reboot... well, we'll see :D

---

