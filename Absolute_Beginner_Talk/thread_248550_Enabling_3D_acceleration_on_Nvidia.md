---
title: "Enabling 3D acceleration on Nvidia"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by SteelCore on 2006-09-01
Hi,
According to the System>Administration>Device Manager my graphics card is a "NV18 [GeForce4 MX 4000 AGP 8x]".  Inorder to enable 3D acceleration should I use nvidia-glx or nvidia-glx-legacy.  Thank you

---

### Post by Kobalt on 2006-09-01
Hello,

Nvidia-glx should suffice.

Cheerios !

---

### Post by SteelCore on 2006-09-02
I installed nvidia-glx successfully.  I then (according to the Ubuntu Guide) ran the command [sudo nvidia-glx-config enable] BUT I got the following error:
BBBBB@Linux-desktop:~$ sudo nvidia-glx-config enable
Password:

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
BBBBB@Linux-desktop:~$

---

### Post by Perfect Storm on 2006-09-02
```
sudo nano /etc/X11/xorg.conf
```

In "section Device" change "nv" to "nvidia"

save and exit, then restart X.

---

### Post by SteelCore on 2006-09-02
Thanks but what does "restart X" mean?

---

### Post by Perfect Storm on 2006-09-02
the xserver.

Your desktop environment.
Log out and press <ctrl>+<alt>+<backspace>
The only time you need to reboot a Linux system is if you make changes to the core.

---

### Post by SteelCore on 2006-09-02
I did change it to 'nvidia' 
" Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection"

and I also restarted X as you explained but on 'sudo nvidia-glx-config enable' I still get the same error message 
"Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia."

---

### Post by Perfect Storm on 2006-09-02
You don't need to run 'sudo nvidia-glx-config enable' if you change the "nv" to "nvidia" in the xorg.conf. You should now see nvidia logo on a reboot or starting X.

---

### Post by SteelCore on 2006-09-02
You're right.  It did work.

BBBBB@Linux-desktop:~$ glxinfo | grep rendering
direct rendering: Yes :D 

THANKS

---

### Post by Rhemat on 2006-09-08
I was recently able to get the nvidia drivers to work, but they seem to be running slower than they did on a previous install.  [glxinfo | grep rendering] returns yes, but it is just going rather slow.  The nvidia section of my xorg.conf is as follows:

Section "Device"
	Identifier	"NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

If you need the whole xorg.conf or other sections let me know.  I know I'm supposed to put another piece into that area, but I've crashed xorg atleast 3 times before, so I'm afraid to tinker (without any guidance, anyway).  Any info would be greatly appreciated.

-Rhemat

---

### Post by Perfect Storm on 2006-09-08
That looks okay. What you mean slow?
Did you made backups of xorg.conf first?
You installed the correct driver? TNT 2 uses nvidia-glx-legacy.

---

### Post by Rhemat on 2006-09-08
I installed the legacy drivers, but I don't even think it's going 100 fps.  I'll have to run Quake3 to get it's framerate, since glxgears doesn't give a readout of frames anymore (or I don't know the command to do such).

Thank you.

-Rhemat

---

### Post by zxee on 2006-09-08
> **Rhemat said:**
> I installed the legacy drivers, but I don't even think it's going 100 fps.  I'll have to run Quake3 to get it's framerate, since glxgears doesn't give a readout of frames anymore (or I don't know the command to do such).

Thank you.

-Rhemat

To get fps (in a terminal) type > glxgears -printfps 

---

### Post by Rhemat on 2006-09-08
Okay, I'm getting close to 200fps, and since it was running smooth, I thought it was slow.  Yeah, I know, pathetic to most peoples systems, but most of my stuff was given to me out of the charity of other peoples hearts.

Thanks.

-Rhemat

---

### Post by laguna321 on 2008-03-12
[COLOR="Red"]Hi Guys i am new here and i was just reading through the posts and i have also followed whatever was written but  apart from this my problem is different. when i installed PlayOnLinux to install safari it told me that my 3d acceleration is not enabled is this true or is it because the directx is not enabled. i have included my Xconf file below for refernce. Thankx in advance[/COLOR]




# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Apr 16 20:37:13 PDT 2007

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
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

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Acer"
	Modelname	"Acer AL1916W"
	Horizsync	30.0-82.0
	Vertrefresh	56.0-76.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

Section "Monitor"
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"NVIDIA GeForce 6 Series"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Device"
	Identifier	"device1"
	Boardname	"NVIDIA GeForce 6 Series"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	1
	Vendorname	"NVIDIA"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	Option		"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Depth	24
		Virtual	1600	1200
		Modes		"1280x1024@60"	"1280x960@75"	"1280x960@60"	"1400x1050@60"	"1280x1024@75"	"1400x1050@75"	"1152x864@75"	"1600x1200@65"	"1024x768@60"	"1600x1200@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "Screen"
	#  
	Identifier	"screen1"
	Device		"device1"
	Monitor		"monitor1"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "ServerFlags"
EndSection

---

### Post by forrestcupp on 2008-03-12
I looks right.  Did you restart after you made these changes?  If so, open a terminal and type:
```
glxinfo | grep direct
```
If it says 'direct rendering = yes', then you're ok.

However, this is a very old thread, and now the easy way to install the nvidia drivers is to go to System->Administration->Restricted Drivers Manager and just check the box to enable the restricted drivers for your nvidia card.

By the way, we don't have DirectX in Linux.

---

