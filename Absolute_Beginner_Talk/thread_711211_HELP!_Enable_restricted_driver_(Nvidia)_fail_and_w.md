---
title: "HELP! Enable restricted driver (Nvidia) fail and window died..."
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by incen on 2008-02-29
Hi, I just wanted to try if my PC can run the 3D effect. So I went to Apperance Preference and selected 'Normal' effect. Then, it wanted me to enable the restricted driver of my graphic card. I did and an error showed. I check the detail:

```
(Reading database ... 97778 files and directories currently installed.)
Removing nvidia-settings ...
Selecting previously deselected package nvidia-glx-new.
(Reading database ... 97757 files and directories currently installed.)
Unpacking nvidia-glx-new (from .../nvidia-glx-new_100.14.19+2.6.22.4-14.10_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.10_amd64.deb (--unpack):
 trying to overwrite `/usr/bin/nvidia-xconfig', which is also in package nvidia-xconfig
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.10_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```

**[SOLVED]** Now, the appearance preference window is even dead. How can I kill it?

Thanks!

---

### Post by jan quark on 2008-02-29
what happens when you run

```
sudo dpkg --configure -a
```

---

### Post by incen on 2008-02-29
Nothing has happened...  :???:

```
cissi@dude:~$ sudo dpkg --configure -a
cissi@dude:~$ 
```

---

### Post by incen on 2008-02-29
This is what the error message is...

```
E: /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.10_amd64.deb: trying to overwrite `/usr/bin/nvidia-xconfig', which is also in package nvidia-xconfig

```

Hope it helps. I have no clue.

---

### Post by jan quark on 2008-02-29
```
sudo dpkg --configure -a
```

should reconfigure broken and half installed packages
but when there is no output there were no broken packages obviously what makes your problem a tricky one

---

### Post by erginemr on 2008-02-29
It seems a program incompatibility to me. I am also using an NVIDIA card and have installed nvidia-glx. There is also a package nvidia-xconfig in Synaptic, which is not installed. I believe you have installed it to and it is conflicting with the package nvidia-glx-new.

So, you should open Synaptic, find the package nvidia-xconfig and remove it first. Then, you should be able to install nvidia-glx-new as expected.

---

### Post by SOULRiDER on 2008-02-29
Try doing
```
sudo aptitude purge nvidia-xconfig
```
and finally:
```
sudo aptitude install nvidia-glx-new
```

Dont forget to change the driver in xorg.

---

### Post by incen on 2008-03-03
> **SOULRiDER said:**
> 
Dont forget to change the driver in xorg.

Hi, may I ask what do you mean 'change the driver'?
Did you mean if there is something like nvidia-xconfig then I replace it with nvidia-glx-new? Thanks!

---

### Post by erginemr on 2008-03-03
S/He is probably saying that you need to make sure the device section in the xorg.file says "nvidia", not "nv":

```
Section "Device"
    ...
    Driver         "nvidia"
    ...
EndSection
```

---

### Post by incen on 2008-03-10
Hi, finally I got my PC. I checked the xorg.conf.
The driver is already changed:
```
Section "device" #       
        Identifier      "device1"
        Boardname       "NVIDIA GeForce 7 Series"
        Busid           "PCI:1:0:0"
        Driver          "nvidia"
        Screen  1
        Vendorname      "NVIDIA"
EndSection
```

---

### Post by erginemr on 2008-03-10
So, what is your current status? Did you follow soulrider's suggestion above? Does everything work now?

---

### Post by incen on 2008-03-10
> **SOULRiDER said:**
> Try doing
```
sudo aptitude purge nvidia-xconfig
```
and finally:
```
sudo aptitude install nvidia-glx-new
```

Dont forget to change the driver in xorg.

No offense, but I have to say these two messed all my screen setting. :(
Now, my dual-screen setting failed and two monitors can only show identical content with very low resolution.
Why does this happen to me? ](*,)

---

### Post by erginemr on 2008-03-10
Don't worry. Maybe we can restore your previous settings, if there are backups of your xorg.conf file? What is the outcome of the following directory listing:
```
ls -l /etc/X11
```

---

### Post by incen on 2008-03-10
[http://ubuntuforums.org/showthread.php?t=692827](http://ubuntuforums.org/showthread.php?t=692827)

Within this URL, before I did what PmDematagoda suggested before and made all my setting work. What is the main difference and main goal for doing these steps? :confused:

---

### Post by incen on 2008-03-10
```
app-defaults             xorg.conf.13              xorg.conf.9
cursors                  xorg.conf.14              xorg.conf.back
default-display-manager  xorg.conf.15              xorg.conf.backup
fonts                    xorg.conf.16              xorg.conf.failsafe
rgb.txt                  xorg.conf.2               xorg.conf.failsafe.1
X                        xorg.conf.20080214151158  xorg.conf.failsafe.2
xinit                    xorg.conf.20080214151928  xorg.conf.failsafe.bak
xkb                      xorg.conf.3               Xresources
xorg.conf                xorg.conf.4               xserver
xorg.conf.1              xorg.conf.5               Xsession
xorg.conf.10             xorg.conf.6               Xsession.d
xorg.conf.11             xorg.conf.7               Xsession.options
xorg.conf.12             xorg.conf.8               Xwrapper.config

```

I've done some backup before: .back and .backup, I think, but not this time. I'll try to pull them back.
But I don't know where those .1, .2, ... coming from.

---

### Post by erginemr on 2008-03-10
There are basically two approaches to installing the binary NVIDIA driver. One (which you have tried so far) is to install it via Ubuntu repositories (aka Synaptic) and the other (which PmDematagoda has outlined) is to install it (a *.run package) from the NVIDIA website. This method involves (as he has also pointed out) disabling the Ubuntu's NVidia driver module, as otherwise, it may conflict with the NVIDIA installer you will download later on.

There also is an auto-installer script called ENVY, which does all the hard work for you by grabbing the installer package (*.run) from the NVIDIA web site and doing almost all the settings itself. You can also give it a try:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

It is very popular and has been reported to work in many otherwise desperate situations.

---

### Post by erginemr on 2008-03-10
> **incen said:**
> 
I've done some backup before: .back and .backup, I think, but not this time. I'll try to pull them back.
But I don't know where those .1, .2, ... coming from.

Yes, I suggest you to first try to get back your original settings and then go for PmDematagoda's way if it doesn't work out.

Check the backup with the latest date (just before you installed this driver). The command: "ls -l" should give you the dates.

---

### Post by erginemr on 2008-03-10
On a second thought, I remember having used a config tool at home: "nvdia-settings", that comes with the nvidia-glx-new package installation:
```
Alt+F2 -> nvidia-settings
```

And if my memory serves me correctly, it has settings to configure resolutions and two monitors.

On a final note, the command:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
may set up your dual screen correctly.

But try all these after you back up at least on working config file with:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup
```

This is all I can think of. I hope you will solve it soon.

---

### Post by incen on 2008-03-10
> **erginemr said:**
> Yes, I suggest you to first try to get back your original settings and then go for PmDematagoda's way if it doesn't work out.

Check the backup with the latest date (just before you installed this driver). The command: "ls -l" should give you the dates.

I overwrote the xorg.conf file; however, it didn't work. Now, I cannot even kill the X-Server. It always stops at 'running local boot scripts.' My PC is not working all right now and I can only use my laptop to talk on the forum. :(

---

### Post by incen on 2008-03-10
> **erginemr said:**
> On a second thought, I remember having used a config tool at home: "nvdia-settings", that comes with the nvidia-glx-new package installation:
```
Alt+F2 -> nvidia-settings
```


I overwrote xorg.conf with those created one month ago when the screens were so right.
They don't work at all. Then, both this one and PmDematagoda's suggestion don't work for me now. :? Even with some backups, I cannot even boot into Ubuntu. The computer just died! I don't know what I should do!

---

### Post by incen on 2008-03-10
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
	Identifier	"nVidia Corporation G70 [GeForce 7600 GT]"
	Boardname	"NVIDIA GeForce 7 Series"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Monitor"
	Identifier	"VX922"
	Modelname	"Custom 1"
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

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce 7600 GT]"
	Monitor		"VX922"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1600	1200
		Modes		"1280x1024@60"	"1280x960@75"	"1280x960@60"	"1400x1050@60"	"1280x1024@75"	"1400x1050@75"	"1152x864@75"	"1600x1200@65"	"1024x768@60"	"1600x1200@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
  screen 1 "screen1" leftof "Default Screen"
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
Section "device" # 
	Identifier	"device1"
	Boardname	"NVIDIA GeForce 7 Series"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	1
	Vendorname	"NVIDIA"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1920x1200@60"	"1680x1050@75"	"1680x1050@60"	"1600x1024@60"	"1440x900@60"	"1440x900@75"	"1280x800@60"	"1280x768@75"	"1280x800@75"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"
	EndSubSection
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Vendorname	"Dell"
	Modelname	"Dell 2407WFP (Digital)"
	Horizsync	30.0-83.0
	Vertrefresh	56.0-76.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1680x1050@75" 188.07 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection
Section "ServerFlags"
	Option		"Xinerama"	"true"
EndSection
```

This is the current xorg.conf I have. However, although there's a '1920x1200' option, why doesn't my graphic card pick it and show like that? I tried to reboot my computer to sort of 'reconfigure' xorg.conf. Is that right? If not, how should I do? Please help me. This is really frustrating. :(

---

### Post by incen on 2008-03-10
> **erginemr said:**
> It seems a program incompatibility to me. I am also using an NVIDIA card and have installed nvidia-glx. There is also a package nvidia-xconfig in Synaptic, which is not installed. I believe you have installed it to and it is conflicting with the package nvidia-glx-new. So, you should open Synaptic, find the package nvidia-xconfig and remove it first. Then, you should be able to install nvidia-glx-new as expected.

As I just checked, I don't have nvidia-xconfig installed. So it may not be a problem.

> **PmDematagoda said:**
> 
```
DISABLED_MODULES="nv nvidia_new"
```


Should I change this one as well if I installed nvidia-glx-new?

---

### Post by erginemr on 2008-03-10
OK. Forget about one of your monitors (i.e. disconnect one of them, and leave the one which looks like more generic -> standard, CRT, etc.)

Boot your Ubuntu Live CD. 

If it boots normally, either grab its xorg.conf file to a pen drive and copy to your existing system, or... 

Mount your existing system by double clicking on it in Nautilus (file manager). Run the file manager with root permissions: Alt+F2 -> "gksudo nautilus". And copy the xorg.conf file inside your virtual file system onto the existing one. Unmount your real hard drive by right clicking on it. Reboot your system and see if X server loads.

If it does, report back and we shall carry on from there forward.

One question though:
> Even with some backups, I cannot even boot into Ubuntu. The computer just died! I don't know what I should do!

Do you mean that you cannot boot your computer even into the text mode?

Did you try:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Normally, this command does not produce such a "xorg.conf" output you have listed above.

---

### Post by incen on 2008-03-10
Really thank you for your reply! Right now I've got something but not right. Now they are still identical display. I cannot make my computer recognize the Dell 2407-wfp or ViewSonic VX922 via Screen and Graphics. It just couldn't handle them! I don't know why! So I chose Generic LCD Panel 1280x1024 so now I have some better result. I'll use PC to post xorg.conf in a sec.

```

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
        Load            "glx"
        Load            "GLcore"
        Load            "v4l"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "Failsafe Device"
        Boardname       "vesa"
        Busid           "PCI:1:0:0"
        Driver          "vesa"
        Screen  0
EndSection

Section "Monitor"
        Identifier      "Failsafe Monitor"
        Vendorname      "ViewSonic"
        Modelname       "ViewSonic VX910"
        Horizsync       30-82
        Vertrefresh     50-85
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
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Failsafe Device"
        Monitor         "Failsafe Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes           "1280x1024@75"  "1280x960@60"   "1152x864@75"   "1280x1024@60"  "1024x768@60"   "1280x960@75"   "1024x768@70"   "1400x1050@60"       "1024x768@75"   "1400x1050@75"  "1024x768@85"   "1600x1200@65"  "832x624@75"    "1600x1200@60"  "800x600@60"    "800x600@85"    "800x600@75"    "800x600@72" "800x600@56"    "640x480@85"    "640x480@75"    "640x480@72"    "640x480@60"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
EndSection
Section "device" # 
        Identifier      "device1"
        Boardname       "vesa"
        Busid           "PCI:1:0:0"
        Driver          "vesa"
        Screen  1
EndSection
Section "screen" # 
        Identifier      "screen1"
        Device          "device1"
        Defaultdepth    24
        Monitor         "monitor1"
EndSection
Section "monitor" # 
        Identifier      "monitor1"
        Gamma   1.0
EndSection
Section "ServerFlags"
EndSection

```

---

### Post by erginemr on 2008-03-10
For all that I know, Screen and Graphics is buggy. I had tried it once out of curiosity and it had managed to screw my working graphics...

---

### Post by incen on 2008-03-10
> **erginemr said:**
> For all that I know, Screen and Graphics is buggy. I had tried it once out of curiosity and it had managed to screw my working graphics...

HAHA~ then what should I do? After copying the old xorg.conf file, what should I make xserver reconfigure?

---

### Post by erginemr on 2008-03-10
I can think of two ways, my way or the highway ;)

No, really, one is to try:
Alt+F2 -> nvidia-settings

and the other is to get your hands dirty with the CLI and refer to:
[http://www.ubuntugeek.com/dual-monitors-with-nvidia.html](http://www.ubuntugeek.com/dual-monitors-with-nvidia.html)
[http://ubuntuforums.org/showthread.php?p=1773584](http://ubuntuforums.org/showthread.php?p=1773584)
[http://www.lockergnome.com/linux/2007/06/18/dual-monitors-with-ubuntu/](http://www.lockergnome.com/linux/2007/06/18/dual-monitors-with-ubuntu/)

I also wish screens & graphics worked as expected, which would ease the life of many Ubuntu users out there.

---

### Post by erginemr on 2008-03-11
I can understand that all this lot of info bombarding is very confusing for you. But once you pull through this problem, you will have extensive knowledge on how to fix graphics related problems and find your way out the CLI. 

So, it is worth to work out different alternatives for the same of experience, too. You can still start over and do a clean reinstall, if worse comes to worst.

A few tidbits of information to fill in the blanks:

1- In the section:
```
Section "Device"
        Identifier      "Failsafe Device"
        Boardname       "vesa"
        Busid           "PCI:1:0:0"
        Driver          "vesa"
        Screen  0
EndSection
```

The line with "vesa" indicates that vesa has been selected as the driver. For your card, there can be three selections:

"vesa" -> Failsafe Vesa driver, worst selection

"nv" -> Open-source NVidia driver, OK for mundane tasks and std. desktop applications, mediocre selection

"nvidia" -> Binary NVidia driver, needed for 3D games and desktop effects, best selection

2- NVidia binary driver is not part of the standard install for legal reasons and can be obtained either by letting restricted-drivers-manager install it or by installing "nvidia-glx-new" (for newer cards like GeForce 8 series), "nvidia-glx" (for cards like Geforce MX 400) and "nvidia-glx-legacy" (for older cards such as TNT, Geforce 2, etc.) form Synaptic.

Once you donwload the driver, you need to issue "nvidia-xconfig" to inject the new driver into the xorg.conf file. There is also a graphical tool "nvidia-settings", where you can adjust quite a few settings.

3- Alternatively, there is a binary installer package (*.run) at the NVIDIA web site. You should visit their site and grab the latest Linux driver corresponding to your card and follow this excellent guide to install it:
[http://ubuntuforums.org/showpost.php?p=4304997&postcount=3](http://ubuntuforums.org/showpost.php?p=4304997&postcount=3)

To me, it is not any superior to the "nvidia-glx*" packages provided by Synaptic, except maybe, it is a newer version. But newer doesn't always mean better.

If you decide to follow this method, I also suggest you to uninstall and purge any "nvidia-glx-*" package from Synaptic. If you follow this way, you will need to disable the original NVidia module inside the kernel, lest that it may interfere and cause incompatibility issues between the two NVidia drivers.

```
DISABLED_MODULES="nv nvidia_new"
```

There is also ENVY, a fantastic script that download the correct driver package from NVidia web site (and from ATI website for ATI owners) and installs it for you:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

4- I am not adept at configuring dual monitors at all, as I am using only one monitor, but also know that it involves using "twinview" somehow in the config file. The links I gave you above should give you some background on how to configure it.

5- "Screens and Graphics" at its current state is buggy and sometimes produces unexpected results, such as reporting your refresh rate (... Hz) lower than normal. It gathers this information from the command line (CLI) tool "xrandr", which is not correct itself. So, I wouldn't count on it this much.

6- Luckily, there are other tools available to configure the X server. One such tool is:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
which will try to configure your X server automatically. 

You may also try:
```
sudo dpkg-reconfigure xserver-xorg
```
which will ask you a series of questions including your driver (vesa, nv, etc.) and selected resolutions.

I don't know how they will fare on a dual monitor system, but you should at least give it a try. But before that, back up your original config file.

7- You will need a basis for you to improve. That is, you need a working config file first as a reference and fall-back setting. That's why, I suggested you to use the one that Live CD builds for you (probably with "nv" as the driver and some tolerable settings) as your basis.

---

### Post by incen on 2008-03-12
> **erginemr said:**
> I can think of two ways, my way or the highway ;)
No, really, one is to try:
Alt+F2 -> nvidia-settings


Hi, really thanks for your kindly help! Well... however, I still don't make this working yet. I cannot initiate this function. It says, 
```
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server.
```

I did it last week but nothing happened. I'm going to give it a try again.

As I think, it failed again. I did what it said. However, when I tried to launch nvidia-settings, the error message showed again, which means nothing I did matters, right? :(

---

### Post by incen on 2008-03-12
> **erginemr said:**
> I can understand that all this lot of info bombarding is very confusing for you. But once you pull through this problem, you will have extensive knowledge on how to fix graphics related problems and find your way out the CLI. 

So, it is worth to work out different alternatives for the same of experience, too. You can still start over and do a clean reinstall, if worse comes to worst.

A few tidbits of information to fill in the blanks:

1- In the section:
```
Section "Device"
        Identifier      "Failsafe Device"
        Boardname       "vesa"
        Busid           "PCI:1:0:0"
        Driver          "vesa"
        Screen  0
EndSection
```

The line with "vesa" indicates that vesa has been selected as the driver. For your card, there can be three selections:

"vesa" -> Failsafe Vesa driver, worst selection

"nv" -> Open-source NVidia driver, OK for mundane tasks and std. desktop applications, mediocre selection

"nvidia" -> Binary NVidia driver, needed for 3D games and desktop effects, best selection


One thing really awkward is that even now my xorg.conf (after nvidia-xconfig) looks like this:
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Wed Sep 12 14:29:17 PDT 2007

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
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    Screen      1  "screen1" LeftOf "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "true"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "VX922"
    VendorName     "ViewSonic"
    ModelName      "ViewSonic VX910"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 85.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
    ModeLine       "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
EndSection

Section "Monitor"
 #   
    Identifier     "monitor1"
    VendorName     "Dell"
    ModelName      "Dell 2407WFP (Digital)"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Gamma           1
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
    ModeLine       "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    ModeLine       "1280x800@75" 107.2 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
    ModeLine       "1280x768@75" 103.0 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
    ModeLine       "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    ModeLine       "1440x900@75" 136.5 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
    ModeLine       "1440x900@60" 106.5 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
    ModeLine       "1600x1024@60" 136.4 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
    ModeLine       "1680x1050@60" 147.1 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1680x1050@75" 188.1 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
    ModeLine       "1920x1200@60" 193.2 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
EndSection

Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce 7600 GT]"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 7 Series"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
 #   
    Identifier     "device1"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 7 Series"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G70 [GeForce 7600 GT]"
    Monitor        "VX922"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1600 1200
        Depth       24
        Modes      "1280x1024@60" "1280x960@75" "1280x960@60" "1400x1050@60" "1280x1024@75" "1400x1050@75" "1152x864@75" "1600x1200@65" "1024x768@60" "1600x1200@60" "1024x768@70" "1024x768@75" "1024x768@85" "832x624@75" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56" "640x480@85" "640x480@75" "640x480@72" "640x480@60"
    EndSubSection
EndSection

Section "Screen"
 #   
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200@60" "1680x1050@75" "1680x1050@60" "1600x1024@60" "1440x900@60" "1440x900@75" "1280x800@60" "1280x768@75" "1280x800@75" "1280x720@60" "1280x768@60" "800x600@60" "800x600@75" "800x600@72" "800x600@56"
    EndSubSection
EndSection
```

When I go to Screen and Graphics, the driver still shows 'vesa'!
Also, I tried one of the links you provided, linking to somewhere else with 'TwinView' and searching in Google. I changed my xorg.conf corresponding to those. NO GOOD LUCK yet! ](*,)

---

### Post by incen on 2008-03-14
> **erginemr said:**
> OK. Forget about one of your monitors (i.e. disconnect one of them, and leave the one which looks like more generic -> standard, CRT, etc.)
Boot your Ubuntu Live CD. 
If it boots normally, either grab its xorg.conf file to a pen drive and copy to your existing system, or... 


Hi, I finally got the LiveCD and did what you said. I saved the xorg.conf from /etc/X11 of the virtual system into a thumb disk and copied to the existing system after. Of course, now it works fine with the analog monitor. (It was working fine before doing this even with the Dell digital one, but just twin display. :p) So how should I make configuration now?

Here is the latest xorg.conf:
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
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
	Identifier	"nVidia Corporation G70 [GeForce 7600 GT]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"VX922"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce 7600 GT]"
	Monitor		"VX922"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

Thanks!

---

### Post by erginemr on 2008-03-14
Great! Now you have a working base.

1. Start with backing up your current config file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup
```

2. Install nvidia-glx-new:
```
sudo aptitude install nvidia-glx-new
```

3. Reconfigure your X server:
```
sudo nvidia-xconfig
```
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

4. Restart your X server by changing to another virtual terminal (Ctrl+Alt+F1-6) and by issuing:
```
sudo /etc/init.d/gdm stop
```
```
sudo /etc/init.d/gdm start
```
to see if everything works. At any time, you can go back to the X server screen with Ctrl+Alt+F7.

5. Check your xorg.conf file to make sure that it uses "nvidia", not "nv" as the driver. Check also if Compiz Fusion works by enabling desktop effects. If everything is OK, disable Compiz for the time being.

6. Do your second back up:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup2
```

7. Now is the time to connect your second monitor ([http://accessories.us.dell.com/sna/productdetail.aspx?sku=320-4335](http://accessories.us.dell.com/sna/productdetail.aspx?sku=320-4335)) and restart your system. See if your system automatically recognizes the second monitor. Whatever the outcome, issue:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
to reflect the change in the connected hardware. 

8. Restart your X server as explained above. Check if both screens show up as you expected. Check also the xorg.conf file to make sure that there is a line with "twinview" in it:
```
...
Option &#8220;TwinView&#8221;
...
```

---

### Post by erginemr on 2008-03-14
If my previous post did not help you enable the dual screen setting you have been expecting, then I am afraid that this is the end of my resources. As I may have said before, I have never used dual monitors and do not know how to configure it manually. 

All I can do is to point to some useful resources:

1. The following sites propose several methods to enable dual monitors:
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)
[http://ubuntuforums.org/showthread.php?p=1773584](http://ubuntuforums.org/showthread.php?p=1773584)
[http://www.ubuntugeek.com/dual-monitors-with-nvidia.html](http://www.ubuntugeek.com/dual-monitors-with-nvidia.html)
[http://www.lockergnome.com/linux/2007/06/18/dual-monitors-with-ubuntu/](http://www.lockergnome.com/linux/2007/06/18/dual-monitors-with-ubuntu/)
[http://www.zulustips.com/2007/04/01/dual-monitors-howto.html](http://www.zulustips.com/2007/04/01/dual-monitors-howto.html)

I suggest you to take your time and read all of them thoroughly before any further action. (4th link has a video screencast.)

2. You may still try to enable it graphically by resorting to the nvidia-settings tool, that should have come twith the nvidia-glx-new package:
```
Alt+F2 -> gksudo nvidia-settings
```

You may adjust the resolution of both screens with this tool. The Option "TwinView" setting requires that you enable the binary "nvidia" driver. (see the attached screenshot)

3. With a too optimistic approach (defying Murphy's law ;)), if everything works at this stage, it is time to do your final back up:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup3
```

4. Finally, enable your desktop effects (which was ironically  your initial goal, wasn't it?) to enjoy your dual screen with desktop effects.

5. Last but not least, stay away from the tool "Screens and Graphics" at all costs.

Good luck, friend.

---

### Post by incen on 2008-03-17
> **erginemr said:**
> 
5. Check your xorg.conf file to make sure that it uses "nvidia", not "nv" as the driver. Check also if Compiz Fusion works by enabling desktop effects. If everything is OK, disable Compiz for the time being.


After replacing 'nv' with 'nvidia', I killed the X-server and restarted it. Then, it couldn't configure it right. It showed the window that 'Now your screen is in very low resolution'. I think this means probably nvidia-glx-new doesn't work for me.... Am I right? :(

---

### Post by incen on 2008-03-17
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
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
	Identifier	"nVidia Corporation G70 [GeForce 7600 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"VX922"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce 7600 GT]"
	Monitor		"VX922"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

This is the xorg.conf I have after doing the 5th step; however, the resolution goes down very low. I compared it with the one backed up by nvidia-xconfig. This is not there

```
Section "Module"
    Load           "glx"
EndSection

```
So I added in. However, it doesn't make any difference. Do I need to make it 'glx-new'?

---

### Post by erginemr on 2008-03-17
> **incen said:**
> 
...
```
Section "Module"
    Load           "glx"
EndSection

```
So I added in. However, it doesn't make any difference. Do I need to make it 'glx-new'?

For one; that section is correct, I also have it. The line:
```
    Load           "glx"
```
has nothing to do with "glx-new".

For another failure story from another GeForce 7600 user:
[http://ubuntuforums.org/showthread.php?t=502694](http://ubuntuforums.org/showthread.php?t=502694)

Also make sure that the package "nvidia-kernel-common" has also been installed alongside "nvidia-glx-new" from Synaptic.

I wish I could help... :(

---

### Post by erginemr on 2008-03-17
1. According to this NVDIA supported cards listing:
[http://us.download.nvidia.com/XFree86/Linux-x86/171.06/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/171.06/README/appendix-a.html)

your card falls into the nvidia-glx-new category, but still, no joy for some unknown reason.

2. Retrospecting your previous posts, I have come across this line:
> E: /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.10_amd64.deb: trying to overwrite `/usr/bin/nvidia-xconfig', which is also in package nvidia-xconfig

Are you using Ubuntu 64-bit OS? Is your processor 64 bit? This might be the source of your problems.

3. Also chances are a mis-configured / corrupt debian package in your cache (/var/cache/apt/archives/) may cause problems. So, it is advisable to flush your cache with:
```
sudo aptitude clean
```

and uninstall and reinstall nvidia-glx-new with:
```
sudo aptitude remove nvidia-glx-new
sudo aptitude install nvidia-glx-new
```

4. Alternatively, my previous suggestion on ENVY is still valid:
> ...
There also is an auto-installer script called ENVY, which does all the hard work for you by grabbing the installer package (*.run) from the NVIDIA web site and doing almost all the settings itself. You can also give it a try:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

It is very popular and has been reported to work in many otherwise desperate situations.
...

To try it if you haven't already, you may uninstall nvidia-glx-new from Synaptic or with:
```
sudo aptitude remove nvidia-glx-new
```

and run ENVY to let it install and configure the binary driver package.

5. Finally, the following is a success story by a Geforce Go 7600 user with dual monitors:
[http://www.nvnews.net/vbulletin/showthread.php?t=67887](http://www.nvnews.net/vbulletin/showthread.php?t=67887)

---

### Post by incen on 2008-03-20
> **erginemr said:**
> 
Also make sure that the package "nvidia-kernel-common" has also been installed alongside "nvidia-glx-new" from Synaptic.

I wish I could help... :(

Yes, nvidia-kernel-common is installed. nvidia-glx-new is installed, too. However, when I just checked with 'aptitude', nvidia-glx-new-dev showed 'p'. Does that mean it's not installed? Do I need this?

Thanks, erginemr. I do really appreciate your help. I myself can really hardly go through this. Thank you very much! I'll try to check out the rest and have to run to class now. :p

---

### Post by erginemr on 2008-03-20
You are welcome, I will be more than happy if it works.

"nvidia-glx-new-dev" is a development package, you don't need it. However, if you try Envy, it will try to download the dev packages for xorg to be able to compile the NVIDIA driver for your kernel. So, you had better have an up and running internet for Envy.

Good luck.

---

### Post by incen on 2008-03-26
Hi, I really want to thank you for all your help although I've tried many times (without Envy) and it didn't turn out ok. However, I finally am able to ask some friend coming to help me. NOW, I GOT THEM WORKING!!! Anyway, thank you very much and all you've done is highly appreciated.  :popcorn:

---

### Post by erginemr on 2008-03-26
> **incen said:**
> Hi, I really want to thank you for all your help although I've tried many times (without Envy) and it didn't turn out ok. However, I finally am able to ask some friend coming to help me. NOW, I GOT THEM WORKING!!! Anyway, thank you very much and all you've done is highly appreciated.  :popcorn:

Hi incen, 

My pleasure. It is really difficult to try to help with problems when you are away from the actual computer. All you do is educated shots in the dark. But I am very glad that you have your desktop back. Now you can enjoy beautiful Compiz goodness. :popcorn:

See you in another thread trying to help a newbie together, as you are not newbie any more. ;) 

Take good care! ):P

---

