---
title: "blacklisting onboard graphics"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by recycledhippy on 2008-02-04
I need to blacklist my onboard nvidia graphics can anyone help me out on how to do it?

---

### Post by bumanie on 2008-02-04
You need to know the exact name and model of the onboard graphics card.
> sudo gedit /etc/modprobe.d/blacklist
At the bottom of the list type in your graphics card name and save
You may want confirmation from someone else - I've never tried this with an on board graphics card (but it did work with ipv6 when my internet wouldn't work). You can reverse it if it doesn't work by getting the list up again and removing what you add and re-saving.

---

### Post by spiderbatdad on 2008-02-04
I thought the op needed to blacklist the fglrx module from the original driver as part of the kernel:```
gksudo gedit /etc/default/linux-restricted-modules-common
``````
DISABLED_MODULES="somemodule fglrx"
```

---

### Post by recycledhippy on 2008-02-04
*-display:0             
       description: VGA compatible controller
       product: RV280 [Radeon 9200 PRO]
       vendor: ATI Technologies Inc
       physical id: 6
       bus info: pci@0000:01:06.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: vga bus_master cap_list
       configuration: latency=32 mingnt=8
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV280 [Radeon 9200 PRO] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 6.1
       bus info: pci@0000:01:06.1
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=32 mingnt=8
  *-display
       description: VGA compatible controller
       product: NV18 [GeForce4 MX - nForce GPU]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a3
       width: 32 bits
       clock: 66MHz
       capabilities: vga cap_list
       configuration: latency=32 maxlatency=1 mingnt=5
 The Nividia one is my onboard. What name should I use when I add it to the list?

---

### Post by recycledhippy on 2008-02-04
Maybe I should state the problem I have and why I need to do this. If I try to enable extra in the visual effects it tells me I need to enable 3D acceleration on the Nvidia, but I am using a ATI card in a PCI slot and not the on board Nvidia. the bios to me is set up right it is reading from the pci slot.

---

### Post by spiderbatdad on 2008-02-04
could you explain exactly what you a trying to accomplish? Are you trying to install the proprietary fglrx driver for your graphics card, or something else? It makes a difference.

---

### Post by spiderbatdad on 2008-02-04
i beleive should should follow the example i gave above. Note "somemodule" is just any other, or none. If you were listing multiple, they would just be separated by spaces. You should also add the nvidia card to the modprobe.d blacklist as Bumanie said.

---

### Post by recycledhippy on 2008-02-04
well, thats the thing, Im not sure if ATI is running up to par and I don't know why if I try to enable extra effects it tells me to enable acceleration for Nvidia when Im not using it

---

### Post by spiderbatdad on 2008-02-04
so NV18 looks like it would work fine in /etc/modprobe.d
Have you seen this guide to enabling the proprietary driver for ATI and Nvidia cards:[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

It worked better for me than any other attempts at enabling good acceleration, though it was only great in low graphics mode. My ATI card is older though...Radeon 7500. Worked great with Beryl...sux with compiz-fusion. Anyway good luck, just wanted to let you know about blacklisting the old resrtricted default module, too.

---

### Post by recycledhippy on 2008-02-11
ok I'm a little confused. I tried to add Nvidia to the blacklist but it still shows up in the screens and graphics I'm thinking that it is see both graphic cards and it should only be seeing one if I typed something in wrong please let me know.


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

nvidia_agp

---

### Post by recycledhippy on 2008-02-11
Any help on this?

---

### Post by spiderbatdad on 2008-02-11
try ```
blacklist nvidia_agp
``` in /etc/modprobe.d/aliases...  also:what does ```
fglrxinfo
``` produce?

---

### Post by recycledhippy on 2008-02-12
also:what does
Code:

fglrxinfo


jason@jason-desktop:~$ fglrxinfo
The program 'fglrxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install xorg-driver-fglrx
bash: fglrxinfo: command not found
jason@jason-desktop:~$

---

### Post by rkd on 2008-02-12
Did you check the BIOS to see whether there is a way to disable the onboard video controller?  If I misunderstand what you are trying to do and that isn't appropriate, just ignore this post.

---

### Post by recycledhippy on 2008-02-12
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

blacklist nvidia_agp


as you can see its on the blacklist but it still shows up in lshw. this is bugging me!! Bios is right, and I tried to do envy but it said it didn't support my ATI card. what else can I do? is there some other way to disable the onboard nvidia? and how can I tell if my ATI card is running the way it should?

---

### Post by rkd on 2008-02-12
Have you tried looking at the output from lsmod to see whether perhaps some other module is requiring nvidia_agp? Perhaps you need to blacklist more than just it.

Something pretty crude would be to move the nvidia_agp module out of the module directory -- that would keep it from loading! Have your live CD handy in case that makes everything stop working, though.

---

### Post by AnonCat on 2008-02-12
Try adding this line to your blacklist file:

blacklist agpgart
blacklist nvidia_agp

---

### Post by BenlsBool on 2008-02-12
thingading ding

---

### Post by recycledhippy on 2008-02-13
OK I was going to try some things today to get the nvidia graphics to go away. I had some updates to do, so I ran them did a restart and something interesting popped up. A restricted driver notice, so I clicked on it, it was the restricted driver notice about nvidia drivers and it said that this card(onboard) was in use? Im not using this card I have an ATI Radeon 9250. any thoughts?

---

### Post by recycledhippy on 2008-02-14
any ideas?

---

### Post by rkd on 2008-02-14
Ideas? Nothing specific. Perhaps there is something odd about the model of motherboard in your computer. How about posting the make and model number, then we can search for other problem reports about it?

---

### Post by jaytek13 on 2008-02-14
> **rkd said:**
> Did you check the BIOS to see whether there is a way to disable the onboard video controller?  If I misunderstand what you are trying to do and that isn't appropriate, just ignore this post.

It doesn't seem you've answered this question. This is the normal way to disable an onboard graphics card and use a different one. We've gotten caught up in blacklisting drivers, but the first step should always be to disable the onboard graphics in the BIOS. Simply blacklisting the driver won't work at all... it just won't load the driver, but your computer will still be using the onboard graphics card, driverless or not.

---

### Post by rkd on 2008-02-14
Back in post #15, he did say "Bios is right", which I interpreted to mean that he did disable the integrated graphics in the BIOS.

That's why I asked just a few minutes ago for the make and model of the motherboard, so we can see whether there are problems disabling its integrated graphics.

---

### Post by recycledhippy on 2008-02-15
ok I just doubled check the bios and it is set up to use the pci slot. In bios I have choice of either pci slot or agp/onboard. Pci is check. As far as the motherboard, I'll have to look into that. the computer is a Emachine T3256 AMD athlon 3200+ with Nvidia geforce4 built in graphics

---

### Post by gfk on 2008-02-16
hi,

You may have to edit your xorg.conf file, which is located in "/etc/X11/xorg.conf", to use the ATI drivers.

You can use any text editor to do the job.

The file basically tells x or whatever which drivers to use for your graphics card, what layout for your keyboard, what kind of mouse your using, the details of modes your monitors support and other misc things.

So i guess yours must be configured to use the onboard nvidia and just have to change it.

---

### Post by nittanylion on 2008-02-16
Ok, this is silly, but are you sure the monitor is plugged in to the right card? 

Shouldn't xorg-driver-fglrx be installed and in use if it's ati card is managing the X server? Unless you're using open source drivers, maybe trying to install xorg-driver-fglrx will provide some nifty and informative error messages....

---

### Post by recycledhippy on 2008-02-16
ok so how sdo I get xorg-driver-fglrx ? And yes my monitor is plugged into the right card. I may be new to ubuntu but I'm not that new

---

### Post by nittanylion on 2008-02-16
I've spent many hours trying to fix a problem that would have been solved had I just gone through the basics first... so you never know, had to ask. I was hoping someone else would chime in on this, because I'd hate to tell you to do something you shouldn't. 

My suggestion to install the fglrx driver from the repository was because it will make the necessary changes to /etc/X11/xorg.conf to ensure that the fglrx driver is used. If the Restricted Drivers Manager reports that the ATI Propreitary Driver is "Enabled" and "In Use," and you still get the Nvidia error message, there is problem with Compiz (Desktop Effects) detecting the correct driver. The downside of this approach is if you install fglrx, there are additional steps you *must *take to enable desktop effects.

(Just a thought here to someone more in-the-know than myself: Is it possible that since Compiz blacklists ATI drivers, it detects the Nvidia card, and just wants to use that card -- regardless if it's actually being used????)

---

### Post by gfk on 2008-02-17
Can you post your xorg.conf file?

I don't think he can use the fglrx drivers.  Do you mean ati's offical drivers in that case he can't that drop support for those cards.  He would then have to use the open drivers, which I use because them for my card, a 9250, like his.  There is a driver available in the repositority but I haven't tried them.

I think the drivers he should be using is the open radeon drivers which is built in.

I done this sort of thing because I don't have no on-board graphics in my morthboard but I'm think you just need to edited your xorg.conf file to use the radeon driver.

You can find the file in /etc/X11/xorg.conf, open it a text editor and post it here.

I can have a look and see.

---

### Post by recycledhippy on 2008-02-17
Now I feel really stupid! where do I find /etc/x11/xorg.conf? I can't seem to locate it

---

### Post by recycledhippy on 2008-02-17
WAIT I got it,
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
	Identifier	"ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Boardname	"ati"
	Busid		"PCI:1:6:0"
	Driver		"ati"
	Screen	0
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"HW191A"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1440x900"
	Horizsync	31.5-56.0
	Vertrefresh	56.0	-	65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Monitor		"HW191A"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1440	900
		Modes		"1440x900@60"	"1280x800@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"
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
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" #        
	Identifier	"device1"
	Boardname	"ati"
	Busid		"PCI:1:6:0"
	Driver		"ati"
	Screen	1
	Option		"MergedFB"	"off"
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
Section "device" #        
	Identifier	"device2"
	Boardname	"NVIDIA GeForce4 (generic)"
	Busid		"PCI:2:0:0"
	Driver		"nv"
	Screen	0
	Vendorname	"NVIDIA"
EndSection
Section "screen" #        
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
EndSection
Section "monitor" #        
	Identifier	"monitor2"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
Section "Extensions"
EndSection

---

### Post by woZa on 2008-02-17
this doesn't really help your specific case but /etc/modules.d/blacklist seems to be broken in Gutsy. I can't prevent any modules from loading using it... Very annoying.

---

### Post by gfk on 2008-02-17
I'm not to sure, really I'm just guessing.

However I have searched and found this which kinda confirmed my thinking.

[http://ubuntuforums.org/showthread.php?t=635943&highlight=disabling+onboard+graphics](http://ubuntuforums.org/showthread.php?t=635943&highlight=disabling+onboard+graphics)


Looking at your xorg doesn't seem wrong.

So you could try and replace your xorg with this xorg

> **recycledhippy said:**
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
	Identifier	"ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Boardname	"ati"
	Busid		"PCI:1:6:0"
	Driver		"ati"
	Screen	0
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"HW191A"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1440x900"
	Horizsync	31.5-56.0
	Vertrefresh	56.0	-	65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Monitor		"HW191A"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1440	900
		Modes		"1440x900@60"	"1280x800@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"
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
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" #        
	Identifier	"device1"
	Boardname	"ati"
	Busid		"PCI:1:6:0"
	Driver		"ati"
	Screen	1
	Option		"MergedFB"	"off"
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
#Section "device" #        
#	Identifier	"device2"
#	Boardname	"NVIDIA GeForce4 (generic)"
#	Busid		"PCI:2:0:0"
#	Driver		"nv"
#	Screen	0
#	Vendorname	"NVIDIA"
#EndSection
#Section "screen" #        
#	Identifier	"screen2"
#	Device		"device2"
#	Defaultdepth	24
#	Monitor		"monitor2"
#EndSection
#Section "monitor" #        
#	Identifier	"monitor2"
#	Gamma	1.0
#EndSection
Section "ServerFlags"
EndSection
Section "Extensions"
EndSection

What I did was to comment out all refrences to the onboard graphics.  Just open up the file and replace all the content.  I am hoping that xserver will then skip it your onboard and use the ati instead.
I haven't done this sort of thing though but it would be what I would do.


Just incase you do try it and it doesn't work.  You should write this down onto some paper so you won't forget 

> dpkg-reconfigure xserver-xorg

and you will need these details of your card so write these down, use when it ask you your card details.

> *product: RV280 [Radeon 9200 PRO]
vendor: ATI Technologies Inc
physical id: 6
bus info: pci@0000:01:06.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: vga bus_master cap_list
configuration: latency=32 mingnt=8
*-display:1 UNCLAIMED
description: Display controller
product: RV280 [Radeon 9200 PRO] (Secondary)
vendor: ATI Technologies Inc
physical id: 6.1
bus info: pci@0000:01:06.1
version: 01
width: 32 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=32 mingnt=8

Just enter that in recovery mode avaiilble at the grub menu.

Infact I am thinking you should use this first.  It will reconfigure your xserver.  Here's why I think that this is what you should do first because it should allow you to chose the ati card over the onboard.

It can be abit daunting the process because it can go pretty techical so I suggest you should google xorg and dpkg-reconfigure xserver-xorg.  Then you can have abit of knowledge on what to do.

Although it you do something wrong you could just redo the whole thing again and try again.  


Before that you could try your original ideal blacklisting "nv" module because that is what your onboard is using.  You can see under "driver" in your xorg.conf file.

I do recommend looking at the link and searching more here with the terms "disabling onboard graphics" before you do the things I suggested.

---

### Post by gfk on 2008-02-17
Here is a another link to the edited xorg except it's formatted proper [LINK]("http://www.shaunchenh.pwp.blueyonder.co.uk/editedxorg") if you decide to do that.

---

### Post by rkd on 2008-02-18
> **recycledhippy said:**
> ok I just doubled check the bios and it is set up to use the pci slot. In bios I have choice of either pci slot or agp/onboard. Pci is check. As far as the motherboard, I'll have to look into that. the computer is a Emachine T3256 AMD athlon 3200+ with Nvidia geforce4 built in graphics

I finally got some information from EMachines technical support about disabling the onboard graphics controller.  They don't really know anything about the motherboard, but finally were able to point me to a web site that had the motherboard manual.

Assuming it actually is the manual for the motherboard you have, I think you misunderstand that BIOS setting, at least if you are talking about the setting I think you are.  The manual says:

**Primary Video Adapter**
The feature allows users to select which display device full on first if two display device onboard.
The options are: PCI Slot, AGP/Onboard.

The grammar isn't quite clear (... which device full on first ...), but I think it is pretty clear that this option does NOT disable the onboard graphics controller when you select PCI.  It merely makes the PCI graphics controller the primary one, and I imagine that priority is only honored by the BIOS.

The manual does not describe any way to disable the onboard graphics controller, at least I didn't see anything like that.

There is one other option it might be worthwhile to check.  Just above the Primary Video Adapter option there is another option named Onboard Video Memory.  This is supposed to be used to control how much system memory is reserved for the onboard graphics controller to use.  The manual says the possible values you can choose are 8M, 16M, 32M, 64M, and 128M.  If I were designing that motherboard, I think I'd be tempted to use that option to provide a way to turn off the onboard graphics controller, perhaps by setting the amount of memory to 0 or some special DISABLED or OFF state.  Since the manual doesn't mention it, it probably doesn't have that possibility, but I encourage you to check what values the BIOS offers for that option.

If you can use that option to disable the onboard graphics, that might not immediately solve your problem, but I think it would be a big step in the right direction.

Of course, if just removing the references to the onboard graphics from xorg.conf, as gfk suggests, fixes the problem, then you don't have to fiddle with this approach.

---

### Post by recycledhippy on 2008-02-18
Thanks soooo much for the info and investicating I'll have to try this stuff it'll probally take me forever and i'll let you know the outcome when I do it!!!

---

### Post by gfk on 2008-02-18
Yeah I now thinking that actually maybe just using:

```
dpkg-reconfigure xserver-xorg
```

and selecting ati though however you will have to also configure your monitor, mouse, keyboard and others so you should search on the code here on google, ubuntu site and forums for maybe a walkthrough.


My second thing is that you should make a backup of your xorg.conf.  Do so by doing this in the terminal:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```

and if you want to restore the file just use this:

```
sudo cp /etc/X11xorg.conf-backup /etc/X11/xorg.conf
```

---

### Post by gfk on 2008-02-19
Oh yeah if you don't know how to restart your system from the command line, use this:

```
sudo shutdown -r now
```

You may need it for when in recovery mode.


You can run that dpkg-reconfigure xserver-xorg code from your terminal at any time.  You then have to restart the x server, to do simply <CTRL><ALT><BACKSPACE> or just restart your system.

---

