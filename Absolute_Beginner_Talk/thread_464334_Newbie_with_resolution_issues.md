---
title: "Newbie with resolution issues"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Mursetablet on 2007-06-04
Hello, as stated above I am completely new to the whole Ubuntu system but I am interested in learning. The issue I have is a resolution problem on a Eurocom T200V convertible tablet that I installed the Ubuntu 7.04 on. When booting up Ubuntu writing etc. is clean and crisp but when it gets to the desktop the resolution is stuck on 800 * 600 at 61 Htz I have tried to bump it up with an "xorg" reconfigure but it always comes back to the same 800 * 600. Now I must admit that I am not really understanding what I am doing I am just blindly following other forum ideas on how to fix the issue. I have seen a lot of posts that are talking of changing codes and inputing computer specific values. I do not know how to access most of the code lines that they say to change ( like do I have to access code changes through the recovery mode of the Grub boot options?), so if someone can point me to a more step by step process that would be helpful. I would like to fix the desktop resolution trouble then look at getting the touch screen up and running.
Here is the information that I have about my system:

Product Specs  	EUROCOM T200V/T210V Convertible
General Information 	 
Launch Date 	August 15, 2003
Phase Out Date 	Current
Colour 	Silver
Supported O/S 	Windows XP Home/Professional
Special Feature(s) 	World's first 14.1" Convertible notebook with rotating display
System Architecture 	 
Spindle Design 	2; HDD
System Architecture 	PC'2001
Main Chipset 	VT8235+CLE266CE
System Bus/FSB 	266 MHz
BIOS Size/Name 	ACPI 4MB Flash ROM
Processor 	 
Processor Make/Class 	VIA Antaur
Socket Type/Spec 	Surface-Mount (SMT)
Processor Speed(s) 	1GHz
Cache (L1/L2) 	L2: 256KB
Video and Graphics 	 
Video Memory/Type 	Shared; up to 32MB
Video Architecture/Chipset 	Integrated
Built-in PC Camera 	optional
Display 	 
LCD size/type/resolution 	14.1" XGA Touch Screen
Memory 	 
Maximum RAM/# of sockets 	1 GB; 2
RAM Type/Spec/Pinout 	DDR333/400
RAM Configuration(s) 	1GB; 512/256MB
Storage 	 
Hard Drives: total # ; max capacity/rpm 	1; 100GB
1st HDD: Max capacity/height/interface 	80GB; 9.5mm; ATA100
2nd HDD: Max capacity/height/interface 	N/A
3rd HDD: Max capacity/height/interface 	N/A
4th HDD: Max capacity/height/interface 	N/A
Card Reader/Type 	SD/MMC/MS/SM 4-in-1; internal
Internal Floppy Drive 	N/A
1st Optical Drive Bay height/options 	external via USB
2nd Optical Drive Bay/Height 	N/A
DVD-ROM Module 	external 8x
CD-Burner (WxRWxR) 	24x
Combo DVD-ROM/CD-RW DVDxWxRWxR 	24x
DVD-Burner 	N/A
Audio 	 
Audio Architecture 	AC'97 Rev 2.1 Compliant
Audio Chipset/Spec 	.
Internal Speaker(s) 	1
Audio-Out 	N/A
Microphone Audio-in 	1 - mono mic
Headphone Out/Jack 	1; stereo
Built-in Microphone/Spec 	1
Communications 	 
on-board LAN / Chipset 	10/100 Ethernet
Internal Modem Type/ Spec 	56K V90
Internal Wireless LAN spec 	802.11b
Internal Bluetooth 	N/A
PC Card Slot(s) 	 
PC Card Architecture/Chipset 	32-bit CardBus
# of slots/Type/Voltage 	1 type II
Zoom Video Port 	N/A
Internal miniPCI # of slots/Type 	N/A
Interfaces (Ports) 	 
Serial Port 	0
USB # of ports/Version 	2; v.2.0
External Monitor: port type; max resolution 	1
Video-In interface 	N/A
RF-in Port 	 
TV-Out (chipset/spec) 	0
on-board FireWire (IEEE1394) 	0
LAN on-board interface 	RJ45
Parallel Port /Spec 	0
IrDA (location/spec) 	1- front
PS/2 Port 	0
Port Replicator Connector 	via USB
Port for Security Cable and Lock 	1 - MicroSaver
Internal Modem Interface 	1 - RJ11
Built-in Antenna for Wireless LAN 	Yes
Input Devices 	 
Internal Keyboard # of keys / hot keys 	85-keys
Built-in instant keys 	3
Numeric Keypad 	Integrated
Multi-language Keyboard(s) 	Available
Internal Pointing Device 	Touchpad
Battery 	 
1st Battery: # of cells; capacity; life 	6-cells; 3 hours
2nd Battery # of cells; capacity; life 	N/A
Dimensions 	 
Product Dimensions WxDxH (mm) 	313(H) x 265(D) x 26.5~29.5(H)mm
Product Weight (kg) 	1.85 kg / 4.8 lbs. w/battery
Packaging L xWx H / N.W. / G.W. 	.
Included Accessories 	 
AC Adapter/Model #/Max Output 	50W
Carrying Case 	Included
Drivers and Utilities CD 	Included
Extra Accessories 	 
Internal MP3 Player 	N/A
Internal TV Tuner w/Remote 	N/A
Internal IP Sharing Module 	N/A
Extra 1st Battery Pack 	Available
Optional AC Adapter 	50W
Optional 2nd Battery Bracket 	N/A
Optional Car Adapter 	Available
Air and Car Adapter 	by Targus
MPEG-2 H/W 	Integrated
Internal LS-120 Drive 	N/A
Optional Modem 	via PCMCIA slot
Optional Port Replicator 	via USB

Any help would be great but please remember that I am really new to this so Simple is Best.
Thanks

---

### Post by lamalex on 2007-06-04
can you post a copy of your /etc/X11/xorg.conf file here?

---

### Post by Mursetablet on 2007-06-04
Could you please tell me the best way to get the "your /etc/X11/xorg.conf file"?

---

### Post by Rocket2DMn on 2007-06-04
> **Mursetablet said:**
> Could you please tell me the best way to get the "your /etc/X11/xorg.conf file"?

in terminal: "sudo gedit /etc/X11/xorg.conf"
type in your root password when prompted and the file will open.

---

### Post by Dylnuge on 2007-06-04
I would use gksudo, not sudo. And your "root" password is just your password, there is no root password on ubuntu.

Also, while in the terminal, post the results of an lspci.

If you are unaware on how to use the terminal, check out [www.linuxcommand.org](www.linuxcommand.org). Terminal is under Applications -> Accessories -> Terminal.

---

### Post by Mursetablet on 2007-06-04
Hi I took awhile to get results from the searches 
sudo gedit /etc/X11/xorg.conf and 
gksudo gedit /etc/X11/xorg.conf 

The Gedit window came up but **nothing was in it**?????

Also I was unable t  figure out how to do the 
lspci it looked like  search but nothing happened after I hit enter.

---

### Post by tibellus on 2007-06-05
Hi. I have the same problem. With all the Ubuntu distros I've tried, I had the same problem. I only have the resolution of 800x600. Can the monitor be a problem?It's a Samtron 76E. On Vector Linux I never encountered such a problem. I had others, but not this one.:) Some with my wireless modem... which I can't seem to fix it, not even now!

---

### Post by Mursetablet on 2007-06-05
Ok I got the lspci to work here is the result.
leigh@Tablet:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8623 [Apollo CLE266]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:08.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 01)
00:08.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics (rev 03)

And the Xorg

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
	Identifier	"VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic LCD Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics"
	Monitor		"Generic LCD Monitor"
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
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Thanks for all your help so far and I look forward to your help in the future.

---

### Post by Brutus2006 on 2007-06-05
I downloaded Envy it worked like a charm  [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Mursetablet on 2007-06-05
I tried Envy but **it was not able to install neither ATI or Nvidia drivers** and I am a bit nervous to do it manually on my own. Does anyone have an opinion on me installing it manually?

---

### Post by tibellus on 2007-06-06
Does Envy work with some older Nvidia cards?I have this old computer, it's a PII at 400mhz with 160 mb of RAM. Ubuntu works very good on it, the only problem that I encountered was this, related to the resolution.

---

