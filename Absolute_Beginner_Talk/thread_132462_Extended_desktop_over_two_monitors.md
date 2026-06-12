---
title: "Extended desktop over two monitors"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by trufflesniffinpig on 2006-02-18
I have [this computer]("http://www.fujitsu-siemens.co.uk/products/mobile/notebooks/amilo_m_7440.html"), with [this monitor]("http://www.viewsoniceurope.com/uk/Products/LCDX/VX715.htm") attached through an svideo port. 

In Windows, I can press the right mouse button on the desktop, select "properties"; then the "Settings" tab, and tell the computer: 1) that the viewsonic monitor is to the left of the notebook monitor; 2) the resolutions of the two monitors; 3) that I want to extend the desktop onto the second monitor (by clicking the check box). 

It's simple, easy to do, and allows me to use two monitors to display different things, which is really helpful.


How do I do the same in Ubuntu? Please: no jargon and no assuming prior knowledge of Linux processes and terminology.

---

### Post by knalle on 2006-02-18
what graphics card do you hava?

---

### Post by trufflesniffinpig on 2006-02-18
None - the graphics are handled through the Intel graphics chip. 

According to the datasheet (available through the link on the previous post):

> Graphics
Shared memory, integrated in Intel 855GM chipset, up to 64MB
- Intel® Extreme Graphics 2 technology

---

### Post by nalmeth on 2006-02-18
Here are some quick google results, might get you started. Video card is key of course

[http://ubuntuforums.org/archive/index.php/t-82109.html](http://ubuntuforums.org/archive/index.php/t-82109.html)
[http://www.ubuntuforums.org/showthread.php?p=447036&posted=1#post447036](http://www.ubuntuforums.org/showthread.php?p=447036&posted=1#post447036)
[http://www.ubuntuforums.org/showthread.php?p=447036&posted=1#post447036](http://www.ubuntuforums.org/showthread.php?p=447036&posted=1#post447036)
[http://ozlabs.org/~jk/docs/mergefb/](http://ozlabs.org/~jk/docs/mergefb/)

seems like xinerama and mergefb are two apps that do this, but keep diggin

---

### Post by knalle on 2006-02-18
ok, you're in trouble because your graphiccard is a piece of shit you know. but you might be able to pull it of 

search the manuals about adding a second screen to your **/etc/X11/xorg.conf** file

---

### Post by trufflesniffinpig on 2006-02-18
[QUOTE=knalle]ok, you're in trouble because your graphiccard is a piece of shit you know. but you might be able to pull it of 

search the manuals about adding a second screen to your **/etc/X11/xorg.conf** file[/QUOTE]

Erm, thanks. But the fact I can use it to set up an extended desktop in Windows suggests that's not really the problem, or at least it shouldn't be.

Aren't there any comparable GUI desktop configuration tools to the one I mentioned at the start of the post? This strikes me as one of those situations where GUIs are ideally suited.

---

### Post by knalle on 2006-02-18
the problem is that Intel, the maker of your graphic card, has yet to provide drivers for linux that supports dual monitors.

sorry for offending your graphics card but in the linux world we still need vendor support for various hardware, and Intel isn't playing along sadly

---

### Post by trufflesniffinpig on 2006-02-18
[QUOTE=knalle]the problem is that Intel, the maker of your graphic card, has yet to provide drivers for linux that supports dual monitors.

sorry for offending your graphics card but in the linux world we still need vendor support for various hardware, and Intel isn't playing along sadly[/QUOTE]


I thought there is [support for Intel integrated graphics chipsets for Linux]("http://www.xfree86.org/current/i810.4.html")? 
Only Intel themselves aren't helping? What problems does that pose?

---

### Post by knalle on 2006-02-18
it is, but not extra support like dual monitors, i dont say that the intel set dont support it, but i know of no other way of enabling it for intel than manually.

if it was **matrox**, **nvidia** or **ati** there are be drivers that supports dual monitors

---

### Post by nalmeth on 2006-02-18
You should be able to do it manually, go over the links I provided

---

### Post by trufflesniffinpig on 2006-02-18
[QUOTE=nalmeth]You should be able to do it manually, go over the links I provided[/QUOTE]

er... I've managed to get it to not work, but in an interesting way!

I set up a Device, Monitor, and Screen section for each monitor, as per [this]("http://www.ubuntuforums.org/showthread.php?p=447036&posted=1#post447036") description, and specified both screens within the ServerLayout section, and got this error message:

EE I810 (0): You must have a MonitorLayout defined for use in a DualHead or Clone setup

...so I looked around and saw that the MonitorLayout section usually goes after the Screen option within the Device section for each monitor, and added this:

Option     "MonitorLayout"     "AUTO, AUTO" 

to both monitor Device sections.

Then I got this message:

(EE) I810 (0): Monitor 1 and 2 cannot be type NONE
 
so I changed the "AUTO, AUTO" part of the "MonitorLayout" option to "LFP, DFP" and got the same message...

Any ideas what the error means and how it can be rectified? (I don't have access to the xorg.conf file because I'm in Windows!)

---

### Post by nalmeth on 2006-02-18
hmm, i wish i actually knew something of use about this. I am interested in this getting resolved, because I want dual monitors too, and I also have a built-in "piece of shit" intel graphics card. Actually its 128 megs, and I don't think its that bad, just not spectacular. I will do some research, and hopefully we'll figure it out

Do you have 3d acceleration enabled? What driver is controlling your card?

---

### Post by trufflesniffinpig on 2006-02-18
I've worked out how to mount a FAT32 formatted USB drive from Unix, to which I've copied the xorg.conf files for looking at in Windows.

The critical parts of the file are:
> 
Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen		0
	Option		"MonitorLayout"		"LFP, DFP"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device_2"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen 		1
	Option		"MonitorLayout"		"LFP, DFP"
EndSection

Section "Monitor"
	Identifier	"Notebook Monitor"
	Option		"DPMS"

EndSection

Section "Monitor"
	Identifier	"ViewSonic Monitor"
	Option 		"DPMS"

EndSection



Section "Screen"
	Identifier	"Notebook Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Notebook Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"ViewSonic Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device_2"
	Monitor		"ViewSonic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Twin_Layout"
	Screen		"Notebook Screen"
	Screen 		"ViewSonic Screen" RightOf "Notebook Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Any advice?

---

### Post by trufflesniffinpig on 2006-02-18
p.s. I know the "Display" subsections in the Screen sections are identical (and wrong). I've just copied and pasted, I just want to get two screens displaying (even one would be good!), and will try to tweak settings afterwards.

---

### Post by trufflesniffinpig on 2006-02-18
[QUOTE=nalmeth]hmm, i wish i actually knew something of use about this. I am interested in this getting resolved, because I want dual monitors too, and I also have a built-in "piece of shit" intel graphics card. Actually its 128 megs, and I don't think its that bad, just not spectacular. I will do some research, and hopefully we'll figure it out

Do you have 3d acceleration enabled? What driver is controlling your card?[/QUOTE]

No 3D acceleration, as far as I know. 

The driver used is i810 (see below - I've pasted the file contents)

---

### Post by trufflesniffinpig on 2006-02-19
OK - still none the wiser.
Any new ideas re: this problem?

---

### Post by nalmeth on 2006-02-19
Can you confirm or deny that your 3Daccel is working? Dual monitors won't work unless the video driver is operational. Well start there from the bottom up

---

### Post by DygitalJoe on 2008-05-02
Hello,

I've been using Ubuntu frequently on my other machines without any issues. I however can't for the life of me configure Ubuntu to work with my work laptop and another LCD Display. 

I've checked almost every article, thread and guide and I'm still lost. I'm asking for an expert here to break it down in simple terms to me about what I should change. 


My system is an HP 8710B Widescreen Laptop; Intel Centrino Duo; Intel on-board Graphics card. My external LCD monitor is also Widescreen and is located on the left side of my laptop. I use the docking station mostly. 

I want the LCD monitor to be the primary and my laptop's screen to be the secondary monitor for unimportant things like Pidgin, XMMS, Thunderbird, etc. 

Here are some commands others have ran to remedy this limitation: 

[B]_My xorg.conf file: _
[/B]```
# xorg.conf (X.Org X Window System server configuration file)
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

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizEdgeScroll"    "0"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Synaptics Touchpad"
EndSection
```
[U]
**~$ xrandr --output LVDS --auto --left-of VGA**[/U]
```
xrandr: screen cannot be larger than 1440x1440 (desired size 2720x900)
```


_**~$ xrandr -q**_
```
Screen 0: minimum 320 x 200, current 1440 x 987, maximum 1440 x 1440
VGA connected 1440x900+0+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1440x900       59.9*+   75.0     59.9  
   1280x1024      75.0     59.9  
   1280x960       59.9  
   1152x864       74.8  
   1024x768       75.1     70.1     65.7     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     65.4     60.0  
   720x400        70.1  
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+   60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right x axis y axis)
```
[U][B]
~$ lspci[/B][/U]
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
02:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b6)
02:04.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 02)
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
18:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)

```

I'm using **Ubuntu "Hardy" 8.04** with all updates. 

Thanks again, any help and guidance is very much appreciated. :)

---

