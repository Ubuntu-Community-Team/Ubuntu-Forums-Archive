---
title: "My sound doesnt work"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Neur0123 on 2007-05-10
Hi
I installed Ubuntu last night, and now my sound doesnt work, but it works fine in windows which i still have installed.
Is there some simple explanation for this or is there something wrong?

Thank you
Neur0123

---

### Post by Kobalt on 2007-05-10
Hello,

Let's try this first : [https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

---

### Post by deadgobby on 2007-05-10
Before you go to above link. Do you have a sound card. If so what kind is it? If you have a sound card like Sound Blaster. Just go into your BIOS and disable the on board sound device. The sound should go through the card. 
 If you are not sure what sound card you have. Please open up your terminal window that can be found in Applications>Terminal.
 Copy and past this command

aplay --list-devices

Please reply of what the list is.

Thanks

---

### Post by Neur0123 on 2007-05-10
**** List of PLAYBACK Hardware Devices ****

Thats all it says when i try that command.
But i think its becouse of the Souns servers, ive read the link above and i cant find Multimedia Systems Selector, its not on the menu, i remember being able to add and remove stuff from the menu but not where i did it......

Neur0123

---

### Post by Kobalt on 2007-05-10
If you need to edit your menus use alacarte : Alt+F2 then enter *alacarte*

---

### Post by drowner on 2007-05-10
> **Neur0123 said:**
> Hi
I installed Ubuntu last night, and now my sound doesnt work, but it works fine in windows which i still have installed.
Is there some simple explanation for this or is there something wrong?

Thank you
Neur0123

Look on the bright side.

Your Keyboard is working 100%.

HTH

Drowner






( LOL ;) )

---

### Post by mills on 2007-05-10
whats the output of 

```
lspci -v
```

---

### Post by Neur0123 on 2007-05-10
Ok i have the multimedia systems selector open now, and there are 3 choices, ALSA, ESD and OSS, in Default Output, and  ALSA, OSS, Test Sound and Silence in Defalt Input.
I have no idea what do use.

Neur0123

---

### Post by Neur0123 on 2007-05-10
Typing: lspci -v

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
        Subsystem: Hewlett-Packard Company Unknown device 2a24
        Flags: bus master, 66MHz, medium devsel, latency 64
        I/O ports at 4100 [disabled] [size=32]
        Memory at <ignored> (64-bit, non-prefetchable)

00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fa000000-fcffffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
        Capabilities: <access denied>

00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Hewlett-Packard Company Unknown device 2a24
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        I/O ports at fe00 [size=8]
        I/O ports at fd00 [size=4]
        I/O ports at fc00 [size=8]
        I/O ports at fb00 [size=4]
        I/O ports at fa00 [size=16]
        Memory at fe02f000 (32-bit, non-prefetchable) [size=512]
        [virtual] Expansion ROM at 80000000 [disabled] [size=512K]
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a24
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a24
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a24
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
        Subsystem: Hewlett-Packard Company Unknown device 2a24
        Flags: 66MHz, medium devsel
        I/O ports at 0500 [size=16]
        Memory at fe02b000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 2a24
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at f800 [size=16]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
        Subsystem: Hewlett-Packard Company Unknown device 2a24
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: d8000000-dfffffff
        Prefetchable memory behind bridge: fde00000-fdefffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GTX] (rev a1) (prog-if 00 [VGA])
        Subsystem: nVidia Corporation Unknown device 02c2
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at fb000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at ef00 [size=128]
        [virtual] Expansion ROM at fc000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
        Subsystem: ASUSTeK Computer Inc. Unknown device 4860
        Flags: bus master, medium devsel, latency 64, IRQ 20
        Memory at dffff000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

02:01.0 Multimedia audio controller: Creative Labs SB X-Fi
        Subsystem: Creative Labs Unknown device 0024
        Flags: bus master, medium devsel, latency 64, IRQ 3
        I/O ports at df00 [size=32]
        Memory at dfc00000 (64-bit, non-prefetchable) [size=2M]
        Memory at d8000000 (64-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>

02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Hewlett-Packard Company Unknown device 2a24
        Flags: bus master, medium devsel, latency 64, IRQ 20
        I/O ports at de00 [size=256]
        Memory at dfffe000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at fde00000 [disabled] [size=64K]
        Capabilities: <access denied>

02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a24
        Flags: bus master, medium devsel, latency 64, IRQ 19
        Memory at dfffd000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at dd00 [size=128]
        Capabilities: <access denied>

02:06.0 Ethernet controller: Atheros Communications, Inc. AR5006X 802.11abg NIC (rev 01)
        Subsystem: Lite-On Communications Inc Unknown device 5001
        Flags: medium devsel, IRQ 20
        Memory at dffe0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>



Sorry for the mass of text.

---

### Post by mills on 2007-05-10
your sound card is detected but iam guessing your drivers aren't installed or running 
[this guide]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide") is pretty good for this

---

### Post by Neur0123 on 2007-05-10
I think i figured out what the problem is now, i have a Creative Sound Blaster X-fi sound card, and there arent any alsa drivers that support it, but if anyone knows if there is some other way to find the drivers please let me know

Thank you for all your help
Neur0123

---

### Post by deadgobby on 2007-05-10
From ASLA web site
Sound Blaster X-Fi  	UNKNOWN  	  	 [X-]
Card delivered to developers. Completely new architecture. Creative actively preventing support due to no datasheets being released to ALSA developers. Reverse engineering work not started due to lack of time.

[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix)

 I'll check more into it and see if some guru found a way to make it work in Linux.

Gobby

---

### Post by nerdman978 on 2007-05-10
Open this file /etc/X11/xorg.conf and post what the file says.
It is an issue with your xorg.conf

---

### Post by Neur0123 on 2007-05-11
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
	Fontpath	"/usr/share/X11/fonts/misc"
	Fontpath	"/usr/share/X11/fonts/cyrillic"
	Fontpath	"/usr/share/X11/fonts/100dpi/:unscaled"
	Fontpath	"/usr/share/X11/fonts/75dpi/:unscaled"
	Fontpath	"/usr/share/X11/fonts/Type1"
	Fontpath	"/usr/share/X11/fonts/100dpi"
	Fontpath	"/usr/share/X11/fonts/75dpi"
	Fontpath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"type1"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/wacom"# Change to 
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
	# /dev/input/event
	# for USB
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/wacom"# Change to 
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
	# /dev/input/event
	# for USB
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/wacom"# Change to 
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
	# /dev/input/event
	# for USB
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"HP L1940"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"HP L1940"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666

---

### Post by deadgobby on 2007-05-12
Xorg has nothing to do with sound. it is for video. Any hoo. I am swamp today. Take the name of your video card and google it. Like 
Creative Labs SB X-Fi linux drivers
or
Creative Labs SB X-Fi unix drivers

---

### Post by deadgobby on 2007-05-13
Well I did some research for your SB X-Fi sound card. You are not going to like it. It is going to be around the 3rd quarter of this year before you can get a linux driver working for it.
[http://opensource.creative.com/soundcard.html](http://opensource.creative.com/soundcard.html)
 Now with that said. You can try installing Open Sound System driver to see if it will work. 
[http://www.4front-tech.com/download.cgi](http://www.4front-tech.com/download.cgi)
 When you DL the deb package Ubie will ask you to open it with GDebi and it will install it.
Hopefully OSS well get it working. Other than that. SB Live cards are pretty cheap.
Gobby

---

### Post by Neur0123 on 2007-05-14
Ok ill see if ill stick with windows until then or maybe get some cheap card.
Thank you for all you help :)

Neur0123

---

