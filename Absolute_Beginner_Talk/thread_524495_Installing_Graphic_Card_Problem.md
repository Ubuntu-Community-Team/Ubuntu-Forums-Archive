---
title: "Installing Graphic Card Problem"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by SH4H4B on 2007-08-13
Hello dear Ubuntu users.

I installed Ubuntu on my laptop which is a Fujitsu Siemens (Amilo Pro v3515) with chipset: via chrome 9 hc igp.
Unfortunately the live-cd didn't detect my graphic card.

I've tried fixing the problem of screen resolution by installing 915resolution program, but I couldn't get my preferred resolution (1280x800)

Does anyone know how I can install the graphic card?

Thanks

---

### Post by Seisen on 2007-08-13
This might help you, 

[http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/]("http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/")

---

### Post by SH4H4B on 2007-08-22
I did as told till decompressing part, " # tar zxvf CN_CX700-CN800XORG40071-kernel-src_[date].tgz"

i got an error then decompressed it myself. still couldn't continue from next step

thanx for your help

---

### Post by SH4H4B on 2007-09-10
By the way, when is the driver going to be supported?

---

### Post by agsamek on 2007-11-08
I've got v3515 and Ubuntu 7.04. You can use vesa driver even though the resolution is not set properly by default. Use command:

sudo dpkg-reconfigure -phigh xserver-xorg

select vesa, then check 1280x800, reboot and it should work.

---

### Post by SH4H4B on 2007-12-04
Thanx! It works fine now, but the keyboard layout on the login screen's changed by default to English and I can't use any other. Any solutions?

---

### Post by danketchpel on 2007-12-04
> **agsamek said:**
> I've got v3515 and Ubuntu 7.04. You can use vesa driver even though the resolution is not set properly by default. Use command:

sudo dpkg-reconfigure -phigh xserver-xorg

select vesa, then check 1280x800, reboot and it should work.

I'm trying desperately to get my vesa driver to do 1400 x 1050 (native on my Acer 20" LCD) and it refuses to do anything other than 1024x768.

I'm running a 3DLabs Wildcat VP560 video card. It runs good at the 1024 resolution but I want the 1400 x 1050, preferably in twinview (how I run the system under Win2K), but I'd settle for at least getting to 1400 for now.

I tried the sudo dpkg-reconfigure -phigh xserver-xorg command but no change.

Here's the relevent portion of my current xorg.conf.  The refresh rates are correct for the monitor.

Any help appreciated as I'm making no headway on this one. I'm close to ripping out the card and replacing it with an Nvidia.

Section "Device"
	Identifier	"3D Labs Wildcat VP560"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Acer AL2017"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"3D Labs Wildcat VP560"
	Monitor		"Acer AL2017"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
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
EndSection

Section "DRI"
	Mode	0666
EndSection

---

