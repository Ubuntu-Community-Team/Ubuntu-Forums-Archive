---
title: "Visual Effects"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by defjam1234 on 2007-12-05
hey there
when i try to put the visual effects on extra or normal i get an error simply saying that the effects could not be enabled. Was wondering if this is a hardware issue or something i can fix by an install...thanks

---

### Post by divague on 2007-12-05
could be hardware issue, which graphics card do you have?

---

### Post by defjam1234 on 2007-12-06
i have an ATI Radion graphics card

---

### Post by nae5 on 2007-12-06
post the output of

```
lspci
```

from app>accessories>terminal

---

### Post by short3000y on 2007-12-06
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
04:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
04:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
04:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)



i have the same problem and i run ati mobility radeon 1400

---

### Post by defjam1234 on 2007-12-06
i have an ATI Radion graphics card

---

### Post by defjam1234 on 2007-12-06
alright, saying im a noob is a gross understatement, and am not sure what i need to do with the information you guys have given me haha any more help would be great

---

### Post by defjam1234 on 2007-12-06
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

ok thats what i got

---

### Post by short3000y on 2007-12-06
go to your terminal and insert lspci and post what happens

---

### Post by KhaaL on 2007-12-06
Hmmm... Could you post your xorg.conf file? it's located in /etc/X11/

---

### Post by defjam1234 on 2007-12-06
you're going to have to tell me how to find it....my ineptitude astounds me too hahah

---

### Post by defjam1234 on 2007-12-06
do i have to do this through the terminal or is it something different alltogether?

---

### Post by KhaaL on 2007-12-06
oh. Just open any text editor, go to /etc/X11/xorg.conf

Or you can also simply type:
gedit /etc/X11/xorg.conf 

from a terminal.

---

### Post by defjam1234 on 2007-12-06
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"dbe"
	Load		"dri"
	Load		"v4l"
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
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	0
	Vendorname	"ATI"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Dell"
	Modelname	"Dell 1024x768 Laptop Display Panel"
	Horizsync	31.5-48.5
	Vertrefresh	59.0-75.0
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	768
		Modes		"1280x768@60"	"1280x720@60"	"800x600@60"	"800x600@75"	"800x600@72"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	1
	Vendorname	"ATI"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

Ok so this is what i got after doing what you said

---

### Post by defjam1234 on 2007-12-06
any ideas?

---

### Post by khgiese on 2007-12-06
Like you I been banging my head against the wall trying to figure out both lock ups and why my eye candy effects would not work.

Here is my xorg.conf
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
	Load "glx"
	Load "dbe"
	Load "dri"
	Load "v4l"
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
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier 	"Radeon X300"
	Boardname 	"ATI Radeon (X300)"
	Busid 		"PCI:1:0:0"
	Driver 		"ati"
	Screen 		0
	Vendorname 	"ATI"
EndSection

Section "Monitor"
	Identifier	"Dell Monitor"
	Vendorname	"Dell"
	Modelname	"Dell E177FP"
	Horizsync	31.0-80.0
	Vertrefresh	56.0-75.0
	Gamma	1.0
EndSection

Section "Screen"
	Identifier 	"Default Screen"
	Device 		"Radeon X300"
	Monitor 	"Dell Monitor"
	Defaultdepth 	24
	SubSection 	"Display"
		Depth 24
		Virtual 1280 1024
		Modes "1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier "Default Layout"
	screen 0 "Default Screen" 0 0
	Inputdevice "Generic Keyboard"
	Inputdevice "Configured Mouse"
EndSection
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

Notice I trimmed down the monitor sectionand removed the modeline, comment yours out to test. Also I removed the @refresh rate off the Modes.
This worked for me. not sure if it will for you. BEFORE MAKING ANY CHANGES MAKE A BACKUP of you current xorg.conf file.

---

### Post by defjam1234 on 2007-12-06
could u explain what scripts i need to take out/ insert? i just got ubuntu a few days ago and am still crazy new

---

### Post by celticbhoy on 2007-12-06
[http://ubuntuforums.org/showthread.php?t=515573&highlight=ati+driver](http://ubuntuforums.org/showthread.php?t=515573&highlight=ati+driver)

try this

---

### Post by YuriBCN on 2007-12-13
I get:
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)

---

### Post by ingram on 2007-12-13
Have you tried 

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#ATI_users_and_Compiz](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#ATI_users_and_Compiz)

---

### Post by JimBuntu on 2007-12-13
Go to this link.

[http://ubuntuforums.org/showthread.php?t=639745](http://ubuntuforums.org/showthread.php?t=639745)

I just did this and it worked first time. Follow the directions perfectly. I have the same "integrated graphics" card. The ATI Radeon Xpress 200M. My appearance settings could only be set to normal, otherwise I would get an error message. I used this link, followed the directions perfectly and it worked first time. Now I can enable all graphics.

---

### Post by JimBuntu on 2007-12-13
Sorry, wrong link.

here it is.

[http://ubuntuforums.org/showthread.php?t=580748](http://ubuntuforums.org/showthread.php?t=580748)

---

