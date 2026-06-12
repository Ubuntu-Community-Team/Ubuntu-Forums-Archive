---
title: "1280x768 resolution lacking"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by Illadar on 2007-07-08
I'm more or less completely new to linux. I installed ubuntu a few months ago, and have ever since been trying to figure out why I can't send the resolution to 1280x768. I have tried messing around with xorg.conf, and it has 1280x768 next to 1024x768 on the list of resolutions but I still can't set my resolution to 1280x768. I have tried running the x configure tool, but every time manage to screw something up and not be able to run x. I'm running a gateway m something tablet, with some sort of integrated intel graphics which I can look up if its important. I offer proactive thanks for any help.

The problem has been resolved.

---

### Post by koshari on 2007-07-08
what video chipset do you have and what video drivers are you using?

---

### Post by overdrank on 2007-07-08
> **Illadar said:**
> I'm more or less completely new to linux. I installed ubuntu a few months ago, and have ever since been trying to figure out why I can't send the resolution to 1280x768. I have tried messing around with xorg.conf, and it has 1280x768 next to 1024x768 on the list of resolutions but I still can't set my resolution to 1280x768. I have tried running the x configure tool, but every time manage to screw something up and not be able to run x. I'm running a gateway m something tablet, with some sort of integrated intel graphics which I can look up if its important. I offer proactive thanks for any help.

HI please post the output of this command in the terminal, located under applications, accessories, terminal
```
lspci
```
and if you don't ming this command also
```
 gksudo gedit /etc/X11/xorg.conf
```

---

### Post by alienexplorers on 2007-07-08
You could try adding a modeline into your xorg.conf "monitor" section.  If you have an nvidia card the monitor section may need to look like this:
> Section "Monitor"
    Identifier     "Monitor0"
    HorizSync       28.0 - 70.0
    VertRefresh     43.0 - 120.0
    Modeline     "1280x768_70.00"  94.98  1280 1352 1488 1696  768 769 772 800  -HSync +Vsync
    Option         "UseEdidFreqs" "FALSE"
    Option         "UseEDID" "FALSE"
    Option         "DPMS"
EndSection

If you have an ATI card leave off the UseEDID and UseEdidFreqs lines in the "monitor" section.

---

### Post by Illadar on 2007-07-09
I'm not real sure how to track down the specifics of my graphics card, and drivers. Here is the info that Overdrank asked for.

> 
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 11)
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:09.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
holman@holman-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 11)
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:09.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
> 
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
	Identifier	"Generic Video Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Option		"CheckDesktopGeometry"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x768" "1024x768" "800x600" "640x480"
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

Thanks for all the help people.

---

### Post by overdrank on 2007-07-09
Hi I have found that this link has helped some with that graphics controller
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller
```


Hope this helps good luck !:popcorn:

---

### Post by Illadar on 2007-07-09
I'm trying to follow that guide, but when ever I try to enter any of the comands it kicks out  the following: 
> Intel 800/900 Series VBIOS Hack : version 0.5.2

Unable to obtain the proper IO permissions: Operation not permitted

Should I just be tossing a sudo in there, or is there a deeper problem.

---

### Post by trak87 on 2007-07-09
oops

---

### Post by trak87 on 2007-07-09
1. You have to be sure your monitor and card are capable of higher resolutions first.

2. When you say 1280 x 768... I've never heard of that resolution. Do you mean 1280 x 1024?

You could try this in a terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

Accept all the defaults. When you get to the option to select screen resolutions add 1280x1024. Complete the process. Exit out to the login screen and press Ctrl-Alt-Backspace. This will restart the X (gui) server and you should get the new resolution. You can go into System, Preferences, Screen Resolution and see if you have 1280x1024 and set it there as well.

---

### Post by overdrank on 2007-07-09
> **Illadar said:**
> I'm trying to follow that guide, but when ever I try to enter any of the comands it kicks out  the following: 


Should I just be tossing a sudo in there, or is there a deeper problem.

That is the response after the first command?

---

### Post by John.Michael.Kane on 2007-07-09
First make sure you have the 915resolution package installed before using any of the methods below.  

Should you the 915resolution package already installed, and are still having issues then move on to one of the guides below. 

Make sure you have your manual as you will need it to do the xorg editing. 

[screen refresh rates....]("http://ubuntuforums.org/showthread.php?p=2605716#post2605716") 

[HOWTO: change resolution/refresh rate in Xorg]("http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution")

---

### Post by Illadar on 2007-07-09
Thanks for the help. What Overdrank suggested seem to have worked. so I guest I should edit the thread closed. Again thanks.

---

