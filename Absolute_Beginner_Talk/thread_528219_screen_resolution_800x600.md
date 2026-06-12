---
title: "screen resolution 800x600?"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by garyed on 2007-08-17
I did a fresh install of Edgy after one of XP & now i can't get my screen resolution higher than 800x600. In XP I get 1280x1024 & I'm using Nvidia universal driver. 
I tried downloading a driver from Nvidia but I can't figure out which one to download or how to install it in Ubuntu either. I've got a geforce 2 Nvidia card. 
Any ideas?

---

### Post by Hobo Joe on 2007-08-17
Use Envy to install your drivers. There is a link in my sig.

Once you have done that run the command:
```

sudo nvidia-settings

```
That will have all your options, including resolution.

---

### Post by garyed on 2007-08-17
> **Hobo Joe said:**
> Use Envy to install your drivers. There is a link in my sig.

Once you have done that run the command:
```

sudo nvidia-settings

```
That will have all your options, including resolution.

Thanks for the help but Envy gives me an error when it installs & says:
"ERROR   Dependency is not satisfiable: module assistant"

---

### Post by jdfreshwater on 2007-08-17
dpkg-reconfigure xserver-xorg

Try this command, to rewrite your xorg.conf file.  It gives you a grapical way to do it.  It allows  you to pick multiple screen resolutions in one of the later steps.

---

### Post by Hobo Joe on 2007-08-17
Try this:
```

sudo aptitude install module-assistant

```

---

### Post by anothrguitarist on 2007-08-17
> **garyed said:**
> I did a fresh install of Edgy after one of XP & now i can't get my screen resolution higher than 800x600. In XP I get 1280x1024 & I'm using Nvidia universal driver. 
I tried downloading a driver from Nvidia but I can't figure out which one to download or how to install it in Ubuntu either. I've got a geforce 2 Nvidia card. 
Any ideas?

Try this:

System | Administration | Restricted drivers manager
Check for your driver

If you cannot get that to work, when you are installing ubuntu, type in the information it requires. Then hit <ctrl> <tab> about three times at hit enter. This is the same as clicking the forward button.

Good Luck.

---

### Post by garyed on 2007-08-17
Thanks to all for all the help.
I'm in the process of getting all the updates installed. 
I thought that might help my problem. 
I'm going to try some of the other suggestions too.
I'll post back in a little while on my progress.

---

### Post by garyed on 2007-08-17
Well i tried everything & nothing worked.
I finally got Envy to install but when I use the Nvidia command I get all kinds of errors:


NV-control extension not found on this display
Unable to dtermine number of nvidia  gpu's 
Unable to determine number of nvidia  framelock

Then the nvidia xserver screen comes up but no settings are ther to adjust.

---

### Post by derekr44 on 2007-08-17
> **garyed said:**
> Well i tried everything & nothing worked.
I finally got Envy to install but when I use the Nvidia command I get all kinds of errors:


NV-control extension not found on this display
Unable to dtermine number of nvidia  gpu's 
Unable to determine number of nvidia  framelock

Then the nvidia xserver screen comes up but no settings are ther to adjust.


I am getting the same.  I am running nvidia-glx-legacy for a Go 420 card on a laptop.  I found some instructions [here]("http://ubuntuforums.org/showthread.php?t=138844&highlight=satellite+resolution&page=2") in regards to allowing the Go 420 cards to display at 1024x768, but I can't seem to get nvidia-settings to work.

Here are my errors:
> ERROR: NV-CONTROL extension version 1.6 is too old; the minimimum required
       version is 1.9.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.

Other than that, the Nvidia legacy drivers are loading fine.  I get the Nvidia logo just prior to login and can enable Compiz.  Just can't get resolution higher than 800x600.

---

### Post by alienexplorers on 2007-08-17
Try adding this to your monitor section of xorg.conf

> Section "Monitor"
    Identifier     "Monitor0"
    HorizSync       insert yours
    VertRefresh     insert yours
    ModeLine       "1280x1024_65.00" 119.4 1280 1368 1504 1728 1024 1025 1028 1063
    Option         "UseEdidFreqs" "FALSE"
    Option         "UseEDID" "FALSE"
    Option         "DPMS"
EndSection


A modeline other than the one above can be made by using the gtf modeline generator.  It is located at:
> [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)

---

### Post by derekr44 on 2007-08-18
Tried it... still no change.  Here's my xorg: (nv and vesa drivers allow 1024x768, nvidia binary legacy drivers do not)

> Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
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
	Identifier	"nVidia GeForce 420 Go"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	# 1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
	Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
	Option		"UseEdidFreqs"	"FALSE"
	Option		"UseEDID"	"FALSE"
	Option		"DPMS"
	Horizsync	28-49
	Vertrefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia GeForce 420 Go"
	Monitor		"Generic Monitor"
	Option		"NoLogo"	"false"
	Option		"AddARGBGLXVisuals"	"true"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1024x768"
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
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by garyed on 2007-08-19
I finally found the answer to my problem, at least partially.
I've been using a KVM switch with three computers hooked up, two of which have Edgy on them.
It seems that Edgy only recognizes the monitor if its connected to the first port of the switch which is the default when its first turned on. Any other port & there will only be two resolution options 800x600 or 640x480 even though there are more in xorg.conf. My other Ubuntu computer was on #1 port & worked fine dual booting with Win98 so I figured it was a driver or some configuration problem I was having with my other XP & Ubuntu computer. XP never had a problem but Ubuntu did even though the switch says its Linux compatible.

---

