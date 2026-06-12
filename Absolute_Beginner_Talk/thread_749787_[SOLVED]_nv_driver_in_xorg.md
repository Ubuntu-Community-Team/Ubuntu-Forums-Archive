---
title: "[SOLVED] nv driver in xorg"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by anewguy on 2008-04-08
Okay, with my PNY Verto GeForce 6600GT, the following are current, and I need to know what I have to do to be able to try desktop effects like compiz:

(1) the xorg.conf file has the driver as "nv".  A review of the Xorg.0.log file show it is actually using the "nv" driver.

(2) restricted manager shows the "new" nvidia driver but it is not enabled (I think the "nv" is part of the legacy driver but I don't want to mess things up)

(3) I had a problem showing in the log about the X GLX not found.  I installed the package and now it shows as loading in the log.

(4) I try glxgears and it is says no GLX assigned to screen 0:0

This is all with a fresh install of 7.10, followed by an attempt (failed) to use the restricted driver, followed by Envy (failed) followed by a manual edit of xorg.conf to the the driver type to "nv".

So, how do I get GLX and everything else set up so I can try compiz?

Thanks in advance! :)

---

### Post by scragar on 2008-04-08
nv is a generic driver, the one in the restricted driver manager is the offical(although closed source :(). Try installing that first, then see if you can enable it using

System > Preferences > Appearance

then using the "Visual Effects" tab.

---

### Post by louieb on 2008-04-08
Nvidia FX5200 here.  I use the restricted driver. **nv** is the open source driver. **nvidia** is the name of the restricted driver enabled through System>Administration>Restricted Drivers  .  Works for me no problem.

---

### Post by anewguy on 2008-04-08
Okay, here's what I tried and didn't have success:

(1) modified xorg.conf to say   Driver "nvidia" (didn't restart X yet, just left it running) -> is there some capital letter in there I don't know about?

(2) installed the legacy stuff for nvidia via synaptic which by default removes the nvidia "new"

(3) went into restricted manager and the only thing that showed was the nvidia "new", but it wasn't enabled.  I enabled it, which it turn wiped out the legacy stuff I had just installed and reinstalled the "new".

(4) from a terminal, did  startx with the output piped to a file so I had my own log, which ended up not working right.  There are 2 things it kicks out on the terminal and never starts  X:

*** memory allocation error, then claims it corrects it

*** can't find the nvidia driver file -> again, do I need some special case characters or something?

The end result was that X wouldn't start.

I then went into a terminal window and tried to modprobe the module - it says it's not found even when it shows on the ls command - what's up with that?

dave@dave-desktop:~$ cd /lib/modules/2.6.22-14-generic
dave@dave-desktop:/lib/modules/2.6.22-14-generic$ ls
build    modules.alias        modules.inputmap   modules.seriomap  ubuntu
initrd   modules.ccwmap       modules.isapnpmap  modules.symbols   volatile
kernel   modules.dep          modules.ofmap      modules.usbmap
madwifi  modules.ieee1394map  modules.pcimap     nvidia
dave@dave-desktop:/lib/modules/2.6.22-14-generic$ cd nvidia
dave@dave-desktop:/lib/modules/2.6.22-14-generic/nvidia$ ls
nvidia.ko
dave@dave-desktop:/lib/modules/2.6.22-14-generic/nvidia$ sudo modprobe nvidia.ko
FATAL: Module nvidia.ko not found.
dave@dave-desktop:/lib/modules/2.6.22-14-generic/nvidia$ 

Help??  :)

---

### Post by anewguy on 2008-04-08
bump

---

### Post by redbob on 2008-04-08
Try installing Envy ([www.albertomilone.com/nvidia_scripts1.html](www.albertomilone.com/nvidia_scripts1.html)). I have a computer with this card, it was driving me crazy because this nv-nvidia-restricted-bla-bla... so I installed Envy, executed and voilà!! Even Compiz and Emerald with rain, fire and cube effects born in my desktop!! Good Luck! :)

---

### Post by anewguy on 2008-04-09
> **redbob said:**
> Try installing Envy ([www.albertomilone.com/nvidia_scripts1.html](www.albertomilone.com/nvidia_scripts1.html)). I have a computer with this card, it was driving me crazy because this nv-nvidia-restricted-bla-bla... so I installed Envy, executed and voilà!! Even Compiz and Emerald with rain, fire and cube effects born in my desktop!! Good Luck! :)

I tried Envy and it gave the same results.  I'll try uninstalling the restricted drivers and try Envy again to see what happens.

:)

---

### Post by anewguy on 2008-04-09
Did Envy again, got the same error when I startx:

..
..
..
..
FATAL ERROR inserting nvidia (/lib/modules/2.6.22-14-generic/nvidia/nvidia.ko)
   no such device
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
..
..
..
..


I even tried the Envy manual install option and tried the next-oldest driver instead of the brand new one - same exact problem.  Note that nvidia.ko DOES exist in the indicated path.  If it's trying to tell me that I don't have a card supported by the driver, I'd like to know how it is able to identify it in the install!

When this fails, it goes back to the VESA driver, which doesn't generate a readable GUI now (used to).

Help?

:)

---

### Post by anewguy on 2008-04-09
As a further update and plea for help:

Everything I have read on the web says that this error is saying that it can't find the video card, and suggest setting the system BIOS so that plug and play operating system is set to no and assign interrupt for VGA is set to yes.  My BIOS has those 2 options with 1 additional:  auto configuration or manual configuration (shows a whole list of IRQ's and DMA's set for PCI).  I have tried the suggestion with the auto config on and with auto config off, and it doesn't help.

My card has 256mb of memory, however the only way I can even get it to display a readable GUI is to use the "nv" driver and flash the BIOS on the video card itself to a higher rev., but it then says it only has 128mb.

I'm really stuck here and really need help.  :)

---

### Post by Neo0351 on 2008-04-09
post your xorg.conf please

---

### Post by anewguy on 2008-04-09
> **Neo0351 said:**
> post your xorg.conf please

Note "nvidia" commented out and "nv" active so I can actually do anything - that's the only difference.

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
	Identifier	"nVidia Corporation NV43 [GeForce 6600]"
	Driver		"nv"
#	Driver		"nvidia"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"KDS XF-70"
	Option		"DPMS"
	Horizsync	30-86
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV43 [GeForce 6600]"
	Monitor		"KDS XF-70"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

---

### Post by Neo0351 on 2008-04-09
ok, im not positive all what you need, but i know you will need this, so add this to your xorg

```
Section "Module"
    Load           "glx"
EndSection
```

hope this helps

---

### Post by anewguy on 2008-04-09
> **Neo0351 said:**
> ok, im not positive all what you need, but i know you will need this, so add this to your xorg

```
Section "Module"
    Load           "glx"
EndSection
```

hope this helps

I guess I didn't scroll down enough when I did my copy/paste - that section as shown is at the bottom of my xorg.conf file already.

Thanks

---

### Post by anewguy on 2008-04-09
Does anyone know how a video card such as this is identified to the driver?  Maybe that can be a clue for me to try to find out why it says no device found when I try to modprobe nvidia (apparently if you load the nvidia kernel module there must be a valid nvidia device present???).

When I look at the hardware, it list my video card as:

linux.sysfs_path    string /sys/devices/pic0000:00/0000:00:1.0/0000:01:00.0


xorg.conf has the pci address as 01:00:00


I noticed the linux.sysfs_path has 01 colon 00 DOT 0  whereas the xorg.conf asy 01 colon 00 COLON 00

How do these addresses correspond (or do they?) ??

Thanks

---

### Post by redbob on 2008-04-09
Have you executed? >  sudo /etc/X11/xserver.xorg

---

### Post by redbob on 2008-04-09
Sorry, the correct command is > sudo dpkg-reconfigure xserver-xorg

---

### Post by anewguy on 2008-04-11
Already did the config of xserver, etc..  The problem has been isolated - my old motherboard, Biostar M6TZA, won't allocate the card correctly in the BIOS.  This may have something to do with it only supporting AGP 1.0, I don't know.  I am able to use the card for now with the NV driver.

I bought a used motherboard/cpu from EBay (ABit KT7-RAID, Athlon 1000) and tried that board (needed a larger power supply as well).  With the KT7-RAID the restricted drivers and the driver (1 version back) from nVidia worked fine.  I say worked, because the BIOS on the motherboard apparently didn't support drives over 32gb (my Ubuntu driver is 80gb).  I found an update to the BIOS, applied it, everything went fine.  Went into BIOS setup to change a couple of things, saved the changes, and the board will now only boot maybe 1 in 15 times - the rest of the time it's dead.  SO, I'm back to my old motherboard but at least the mystery with the GeForce 6600GT is solved. :)

BTW - anyone know where I can get the high-tolerance capacitors used on a KT7-RAID?  I found one by the AGP slot that has popped, and 3 by the torroids that look swollen.  :(

---

