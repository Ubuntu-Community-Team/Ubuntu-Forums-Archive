---
title: "login problems"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by mfk on 2007-12-30
Hi, brand new at Ubuntu....Had "everything" working fine, but I was trying to get the desktop effects to work. I figured I should install NVIDA drivers. I pasted a couple of lines into terminal window...it installed some things and deleted one. Nothing seemed to change, but when I tried to login again it would just go back to the login window. I _can_ login using the FAILSAFE  mode...Nothing seem to have changed otherwise. I have no idea where to start or if there is a "system recovery" thing I can do. Can I  see the last changes I made in the terminal window.Thanks

PS. This is what you get when you stay up for two days and try to learn a new system overnight :]

---

### Post by overdrank on 2007-12-30
> **mfk said:**
> Hi, brand new at Ubuntu....Had "everything" working fine, but I was trying to get the desktop effects to work. I figured I should install NVIDA drivers. I pasted a couple of lines into terminal window...it installed some things and deleted one. Nothing seemed to change, but when I tried to login again it would just go back to the login window. I _can_ login using the FAILSAFE  mode...Nothing seem to have changed otherwise. I have no idea where to start or if there is a "system recovery" thing I can do. Can I  see the last changes I made in the terminal window.Thanks

PS. This is what you get when you stay up for two days and try to learn a new system overnight :]

HI and could you tell us the commands you used, you can retrieve the previous commands with the up arrow in the terminal. Also what is the model of the graphics card?

---

### Post by mfk on 2007-12-30
I have an onboard graphics card motherboard VIA KM400A/AM400....the last commands were
michal@X-Factor2:~$ compiz
michal@X-Factor2:~$ SKIP_CHECKS=yes compiz
michal@X-Factor2:~$ sudo apt-get install ubuntu-restricted-extras
michal@X-Factor2:~$ lspci | grep -i nvidia
michal@X-Factor2:~$ sudo apt-get install ubuntu-restricted-extras
michal@X-Factor2:~$ lspci | grep -i nvidia
michal@X-Factor2:~$ sudo apt-get install nvidia-glx-legacy
michal@X-Factor2:~$ sudo apt-get install nvidia-settings
michal@X-Factor2:~$ sudo nvidia-glx-config enable
michal@X-Factor2:~$ sudo apt-get install xserver-xgl compiz-gnome
michal@X-Factor2:~$ compiz
michal@X-Factor2:~$ sudo apt-get update


I know what I did was dump and mostlikely It didn't make sense. Hope you can help

---

### Post by overdrank on 2007-12-30
> **mfk said:**
> I have an onboard graphics card motherboard VIA KM400A/AM400....the last commands were
michal@X-Factor2:~$ compiz
michal@X-Factor2:~$ SKIP_CHECKS=yes compiz
michal@X-Factor2:~$ sudo apt-get install ubuntu-restricted-extras
michal@X-Factor2:~$ lspci | grep -i nvidia
michal@X-Factor2:~$ sudo apt-get install ubuntu-restricted-extras
michal@X-Factor2:~$ lspci | grep -i nvidia
michal@X-Factor2:~$ sudo apt-get install nvidia-glx-legacy
michal@X-Factor2:~$ sudo apt-get install nvidia-settings
michal@X-Factor2:~$ sudo nvidia-glx-config enable
michal@X-Factor2:~$ sudo apt-get install xserver-xgl compiz-gnome
michal@X-Factor2:~$ compiz
michal@X-Factor2:~$ sudo apt-get update


I know what I did was dump and mostlikely It didn't make sense. Hope you can help

Ok could you verify that board I believe uses the unichrome graphics. Please post the out put of the command ```
lspci
``` in the terminal, you can copy and paste
Edit Either way you can reconfigure you xorg with this command ```
 sudo dpkg-reconfigure -phigh xserver-xorg 
``` and that should correct the issue Good luck!

---

### Post by mfk on 2007-12-31
michal@X-Factor2:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:05.0 Network controller: RaLink RT2561/RT61 802.11g PCI
00:06.0 USB Controller: NEC Corporation USB (rev 41)
00:06.1 USB Controller: NEC Corporation USB (rev 41)
00:06.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

---

### Post by overdrank on 2007-12-31
> **mfk said:**
> michal@X-Factor2:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:05.0 Network controller: RaLink RT2561/RT61 802.11g PCI
00:06.0 USB Controller: NEC Corporation USB (rev 41)
00:06.1 USB Controller: NEC Corporation USB (rev 41)
00:06.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

HI and yes the nvidia driver you were trying to install will not work so use the previous command and configure you xorg. good luck!

---

### Post by mfk on 2007-12-31
just paste "sudo dpkg-reconfigure -phigh xserver-xorg"? this should do the trick?

---

### Post by mfk on 2007-12-31
nothing chaged...still not able to login normally....Since this isn't as simple as I hoped it would be, I thnk I will just reinstall everything start fresh  (I don't really have anything saved anyway) So thank you for your time I'll try to be more carefull next time:)

---

### Post by diafygi on 2008-01-01
I am having the same problem as you, and it seems to be narrowed to the installation of xserver-xgl. You shouldn't need XGL for 2D stuff. If you want Compiz-fusion, look on Free Software Magazine's [chart]("http://www.freesoftwaremagazine.com/blogs/bored_with_3d_desktops") for what you need to enable 3d effects for your video card. It says my video card (Nvidia GeForce2 Ultra) should work with XGL, but I can't seem to get XGL to work. So if you have found a solution for this problem that doesn't involve uninstalling XGL, please post it.

[This]("http://ubuntuforums.org/showthread.php?p=4053221#post4053221") is where I'll be posting any solutions I find.

---

### Post by overdrank on 2008-01-01
> **diafygi said:**
> I am having the same problem as you, and it seems to be narrowed to the installation of xserver-xgl. You shouldn't need XGL for 2D stuff. If you want Compiz-fusion, look on Free Software Magazine's [chart]("http://www.freesoftwaremagazine.com/blogs/bored_with_3d_desktops") for what you need to enable 3d effects for your video card. It says my video card (Nvidia GeForce2 Ultra) should work with XGL, but I can't seem to get XGL to work. So if you have found a solution for this problem that doesn't involve uninstalling XGL, please post it.

[This]("http://ubuntuforums.org/showthread.php?p=4053221#post4053221") is where I'll be posting any solutions I find.

Hi can you post your exact model of graphics card and the output of this command ```
cat /etc/X11/xorg.conf
``` please use the code tags in your reply.

---

### Post by diafygi on 2008-01-01
Here's my graphics card model:
```

Vendor: nVidia Corporation
Device: NV15BR [GeForce2 Ultra, Bladerunner]

```

Here's my xorg.conf file contents with XGL installed and Gnome in Failsafe mode:
```

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

Section "Files"
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
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV15BR [GeForce2 Ultra, Bladerunner]"
	Boardname	"NVIDIA Legacy"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Monitor"
	Identifier	"DELL P1110"
	Vendorname	"Dell"
	Modelname	"Dell P1110"
	Horizsync	30.0-121.0
	Vertrefresh	48.0-160.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
  modeline  "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@85" 229.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@75" 261.0 1792 1888 2104 2456 1344 1345 1348 1417 -hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline  "1856x1392@75" 288.0 1856 1984 2208 2560 1392 1393 1396 1500 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
  modeline  "1920x1440@75" 297.0 1920 2064 2288 2640 1440 1441 1444 1500 -hsync +vsync
  modeline  "2048x1536@60" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
  modeline  "2048x1536@75" 340.48 2048 2216 2440 2832 1536 1537 1540 1603 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV15BR [GeForce2 Ultra, Bladerunner]"
	Monitor		"DELL P1110"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	2048	1536
		Modes		"800x600@60"	"832x624@75"	"800x600@85"	"1024x768@85"	"800x600@75"	"1024x768@75"	"800x600@72"	"1024x768@70"	"800x600@56"	"1024x768@60"	"640x480@85"	"1024x768@43"	"640x480@75"	"1152x864@75"	"640x480@72"	"1280x1024@75"	"640x480@60"	"1280x960@60"	"1280x960@85"	"1280x1024@85"	"1280x1024@60"	"1280x960@75"	"1400x1050@60"	"1400x1050@75"	"1600x1200@65"	"1600x1200@60"	"1600x1200@75"	"1600x1200@70"	"1600x1200@85"	"1792x1344@75"	"1792x1344@60"	"1856x1392@60"	"1856x1392@75"	"1920x1440@60"	"1920x1440@75"	"2048x1536@60"	"2048x1536@75"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection

```

Here's my xorg.conf file contents with XGL uninstalled:
```

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

Section "Files"
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
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV15BR [GeForce2 Ultra, Bladerunner]"
	Boardname	"NVIDIA Legacy"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Monitor"
	Identifier	"DELL P1110"
	Vendorname	"Dell"
	Modelname	"Dell P1110"
	Horizsync	30.0-121.0
	Vertrefresh	48.0-160.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
  modeline  "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@85" 229.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@75" 261.0 1792 1888 2104 2456 1344 1345 1348 1417 -hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline  "1856x1392@75" 288.0 1856 1984 2208 2560 1392 1393 1396 1500 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
  modeline  "1920x1440@75" 297.0 1920 2064 2288 2640 1440 1441 1444 1500 -hsync +vsync
  modeline  "2048x1536@60" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
  modeline  "2048x1536@75" 340.48 2048 2216 2440 2832 1536 1537 1540 1603 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV15BR [GeForce2 Ultra, Bladerunner]"
	Monitor		"DELL P1110"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	2048	1536
		Modes		"800x600@60"	"832x624@75"	"800x600@85"	"1024x768@85"	"800x600@75"	"1024x768@75"	"800x600@72"	"1024x768@70"	"800x600@56"	"1024x768@60"	"640x480@85"	"1024x768@43"	"640x480@75"	"1152x864@75"	"640x480@72"	"1280x1024@75"	"640x480@60"	"1280x960@60"	"1280x960@85"	"1280x1024@85"	"1280x1024@60"	"1280x960@75"	"1400x1050@60"	"1400x1050@75"	"1600x1200@65"	"1600x1200@60"	"1600x1200@75"	"1600x1200@70"	"1600x1200@85"	"1792x1344@75"	"1792x1344@60"	"1856x1392@60"	"1856x1392@75"	"1920x1440@60"	"1920x1440@75"	"2048x1536@60"	"2048x1536@75"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection

```

I don't really see where the two are different.

---

### Post by overdrank on 2008-01-01
HI and yes that chart does read that your card is supported in Xorg 7.1 but feisty is using xorg 7.2.  I was replying to help, but the old card I have is geforce 3. So I believe that info on that page is correct  just outdated. Good luck and sorry that I was not of any help.

---

