---
title: "fglrx module compilation problem (installation went fine  but...)"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by mashimaro on 2008-02-21
Hi guys!

Well I just installed ati-driver-installer-8-01-x86.x86_64.run for ATI Radeon 2600HD Pro 512 Mb card. The installation of:
xorg-driver-fglrx_8.452.1-1_i386
xorg-driver-fglrx-dev_8.452.1-1_i386.deb
fglrx-amdcccle_8.452.1-1_i386.deb
went fine. 

The problem was with the fglrx-kernel-source_8.452.1-1_i386.deb
when I run dpkg -i fglrx-kernel-source_8.452.1-1_i386.deb this is what I get.
> Preparing to replace fglrx-kernel-source 8.452.1-1 (using .../fglrx-kernel-source_8.452.1-1_i386.deb) ...
Unpacking replacement fglrx-kernel-source ...
rpmdb: 
Adding Module to DKMS build system
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: urpmdb: nable to lock mutex: Invalid argument
rpmdb: ununable to lock mutex: Invalid argumentable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unablunable to lock mutex: Invalid argumentrpmdb: e to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to unable to lock mutex: Invalid argumentrpmdb: lock mutex: Invalid argument
rpmdb: unable to rpmdb: lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
unable to lock mutex: Invalid argument



unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argumenlock mutex: Invalid argumentt
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to 
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument

Error! DKMS tree already contains: fglrx-8.452.1
You cannot add the same module/version combo more than once.
Doing initial module build
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lockalid argument mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Inv
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument

Error! Your kernel source for kernel 2.6.22-14-386 cannot be found at
/lib/modules/2.6.22-14-386/build or /lib/modules/2.6.22-14-386/source.
Installing initial module
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument
rpmdb: unable to lock mutex: Invalid argument

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.22-14-386 (i686) first.
Done.


I also tried using module-assistant to compile the module but to no avail. 
My kernel version is :2.6.22-14-386
and I am using Ubuntu Gutsy

here is my xorg.conf

> 
# xorg.conf (xorg X Window System server configuration file)
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

Section "ServerLayout"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Option		"AIGLX"	"true"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"type1"
	Load		"vbe"
	Load		"dbe"
	Load		"GLcore"
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
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"S/M 150MP"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	Horizsync	31.5	-	64.0
	Vertrefresh	56.0	-	65.0
	Gamma	1
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc ATI Default Card"
	Driver		"fglrx"
	Boardname	"fglrx"
	Option		"UseInternalAGPGART"	"no"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Busid		"PCI:1:0:0"
	
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc ATI Default Card"
	Monitor		"S/M 150MP"
	Defaultdepth	24
	SubSection "Display"
		Virtual	1280	1024
		Depth	24
		Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection



It boots up fine, no black screen (which was a problem before, and then I discovered that it was because one needs to set up the xorg.conf correctly with the correct monitor settings). This is what I get when I do a fglrxinfo:
> display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)


:popcorn:

Can anyone help me??? Thanks!

P.S. Btw, I already spent 3 days trying different solutions through google. :D

---

### Post by pointone on 2008-02-21
Try following [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide").

---

### Post by mashimaro on 2008-02-21
Thanks for the site, but I still have the same problem.

I followed the same exact site's instructions a couple of times days before, but no results. 

modprobe -a fglrx shows this

WARNING: Error inserting fglrx (/lib/modules/2.6.22-14-386/kernel/drivers/char/drm/fglrx.ko): Invalid module format

when I use module-assistant I get this as an error (after following the linking instruction at the site you gave me: This is what i get when I select BUILD and then VIEW:

> /usr/share/modass/packages/fglrx-kernel-source: 1:  debian/rules: not found

it's not debian of course. 

Well anyways, there "is" a fglrx.ko already in this directory 
/lib/modules/2.6.22-14-386/kernel/drivers/char/drm/fglrx.ko
It's the ati fglrx.ko not the linux-restricted-drivers one, as I deleted everything related to fglrx before installation.

I guess the module isn't loading correctly. help!

---

### Post by white_eagle-mk on 2008-02-24
Dude, just follow this guide  --> [http://ubuntuforums.org/showthread.php?t=589637](http://ubuntuforums.org/showthread.php?t=589637) 
Hope it helps!

---

### Post by mashimaro on 2008-03-05
Hi,

I tried this guide: [http://ubuntuforums.org/showthread.php?t=589637](http://ubuntuforums.org/showthread.php?t=589637) 
just recently. Still doesn't work :/

I still think the problem lies with the compilation of the fglrx kernel and dkms:

> sudo m-a prepare,update

sudo m-a build,install fglrx-kernel
It always fails at this step, anyone else have any ideas? I am stumped (still).

Thanks to everyone who replied!

---

### Post by mashimaro on 2008-03-23
Tried the newest release on the ATI website, same problem. It has been a month now. I'm getting frustrated with Ubuntu now, can anyone help me? 

I was thinking of switching to Fedora if no solution is available. 

I think the only problem is the fgrlx module compilation, and this line "rpmdb: unable to lock mutex: Invalid argument" which is generated by the dkms command. Hope this helps you guys understand my situation.

Thanks again!

---

