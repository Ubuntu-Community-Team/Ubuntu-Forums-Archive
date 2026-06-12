---
title: "Dual monitors"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by jrjr on 2006-07-12
Are dual monitors supported as in Windows?

---

### Post by Brunellus on 2006-07-12
yes, but it requires a bit of work.

[https://help.ubuntu.com/community/XineramaHowTo](https://help.ubuntu.com/community/XineramaHowTo)

---

### Post by orb9220 on 2006-07-12
What Video card do you have?

For nvidia:

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

For ati:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Hope this helps

---

### Post by jrjr on 2006-07-12
Not sure what I am going to install on yet but this machine has an ATI X1600 so it looks like the R400 driver should work. Im looking at an older poweredge maybe but I know little about linux. I installed some distros years ago but don't remember much so I would say im starting from scratch again. To start with I think the desktop version is what I will try and then wipe it and install server later on, or not... can desktop be used for server applications with just some package installs?

---

### Post by Brunellus on 2006-07-12
> **jrjr said:**
> Not sure what I am going to install on yet but this machine has an ATI X1600 so it looks like the R400 driver should work. Im looking at an older poweredge maybe but I know little about linux. I installed some distros years ago but don't remember much so I would say im starting from scratch again. To start with I think the desktop version is what I will try and then wipe it and install server later on, or not... can desktop be used for server applications with just some package installs?
answer is yes.

---

### Post by jrjr on 2006-07-12
Ok, I thought so. What I would end up with is things installed that are not necessary for a server environment is all. I downloaded, burned and booted into Ubuntu from the CD... I am writing from it now! I will play with this for a while and see how it goes. It picked up my sound card and nic with no trouble.. seems a LOT easier than I remember LOL

Will get back on here when I get really serious... thanks

---

### Post by jrjr on 2006-07-15
I must be getting serious! LOL

Which Ubunto do I have X86 or X86_64  ??
How do I tell?  

This page asks:

[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

(then click linux display drivers and software)

---

### Post by jrjr on 2006-07-16
So how do I tell what I have?
I downloaded ubuntu-6.06-desktop-i386.iso
Burned it to CD
Booted from it and installed as dual boot

There must be some way of knowing...

My system includes- 
2.8 P4 Northwood core
ATI X1600


And how do I install this driver?
I downloaded this - ati-driver-installer-8.26.18-x86.run
Thats the non-64 version
Its sitting on my desktop now. 
I dont see a way to use Synaptic

---

### Post by jrjr on 2006-07-16
Well with this page - 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
I got as far as below. Now I need to figure out how to enable the second head......

fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series Generic
OpenGL version string: 2.0.5814 (8.25.18)

---

### Post by Koti on 2006-07-16
I'm in a similiar boat regarding the dual monitor situation. I just installed Ubuntu 6.06. It defaulted to my added PCI video card. Now I'd like to enable to onboard video.

Once I load the driver for the onboard video(not sure what it is yet b/c the computer is a dell and I'll have to dig up the paperwork) will the dual monitor be facilitated or will there be more finagling required?

---

### Post by jrjr on 2006-07-16
I would bet there will be more to do. Check the link in my last post. I just installed yesterday too!!  

My xorg.conf correctly identifies my card. I have found posts where others have been successful but their xorg.conf files are HUGE compared to mine. Must be they have been at this a while :) 

I am not sure what to do exactly as I dont want to loose my video completely and have to start with another ubuntu install, that would suck.

I have been looking at this thread, maybe it will help you too:
[http://www.ubuntuforums.org/showthread.php?t=199574&highlight=enable+head+radeon](http://www.ubuntuforums.org/showthread.php?t=199574&highlight=enable+head+radeon)

---

### Post by h2gofast on 2006-07-16
You won't loose your video completely.  Just backup your xorg.conf
before you edit your xorg.conf

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

This makes a backup copy. If you break your xorg.conf...
login to the command line with your user and password
and type...
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.broken
so you can look at your mistakes. Then...
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
and you're good to go, just restart X or reboot...

sudo reboot

---

### Post by jrjr on 2006-07-16
Thanks, ran the command and printed your post
Now I have to figure out how to open the file so its not read only

I should add too....

Both of my monitors work but they are cloned... need to be one big desktop

---

### Post by Devarien on 2006-07-16
Hello everyone!

I just installed Ubuntu a few days ago and love it so far.  Once I get two issues resolved, my Windows XP partition is getting wiped to make more room for Ubuntu =)

The issue I'm having right now is a dual-screen recognition problem.  I have Xinerama working fine and both monitors are being recognized, so the issue isn't getting Dual Screens working.

Instead, my graphics card wants to think that my external CRT monitor is the primary display device and my laptop LCD is the secondary one - which is really annoying, because the laptop LCD is vastly superior to the CRT, which I only use for select few purposes.

My question is: How do I make xorg.conf recognize the Laptop LCD as the primary monitor and the external CRT monitor as the secondary?  Relevant information below.

Computer: HP Pavilion ZD7200 CTO
GFX: NVIDIA Geforce FX Go5700
Laptop LCD: 17" Widescreen model 394844-001
External CRT: Sony Multiscan 17sf II

and my xorg.conf:

```
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
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
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
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV36 [GeForce FX Go5700]"
	Driver		"nvidia"
	VendorName	"Videocard vendor"
	BoardName	"NVIDIA Geforce FX Go5700"
	BusID		"PCI:1:0:0"
	Option		"NvAGP" "2"
	Option		"NoLogo" "1"
	Option		"RenderAccel" "0"
	Option		"CursorShadow" "1"
	Option		"Coolbits" "1"
	Option		"ConnectedMonitor" "crt,dfp"
	Option		"NoPowerConnectorCheck"
	Option		"Twinview" "1"
	Option		"Metamodes" "1024x768,1024x768"
	Option		"SecondMonitorHorizSync" "28-72"
	Option		"SecondMonitorVertRefresh" "43-60"
#	Option		"NoTwinViewXineramaInfo"
	Option		"Xinerama" "On"
	Option		"CRT2Position" "LeftOf"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV36 [GeForce FX Go5700]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Viewport	0 0
		Depth		1
		Modes		"1440x900" "1024x768"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		4
		Modes		"1440x900" "1024x768"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		8
		Modes		"1440x900" "1024x768"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		15
		Modes		"1440x900" "1024x768"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		16
		Modes		"1440x900" "1024x768"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		24
		Modes		"1440x900" "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"TwinView Configuration"
	Screen		0 "Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama" "Off"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Also, the CRT brightness/contrast are maxed out on the monitor but is still a little dark and hard to look at.  Solutions?

Thanks!

-Dev

---

### Post by jrjr on 2006-07-16
> **jrjr said:**
> Thanks, ran the command and printed your post
Now I have to figure out how to open the file so its not read only

I should add too....

Both of my monitors work but they are cloned... need to be one big desktop

Ok, I ran 
sudo -i
and that got me running as root
Then I tried 
 gedit /etc/X11/xorg.conf
to open the file but no go
I can open it by clicking in gedit but its read only
I dont see anything in xorg.conf that refers to cloned or bigdesktop or anything else like that so I dont know what to edit anyway
What a nOOb   :p

---

### Post by jrjr on 2006-07-16
This is getting ridiclous. I have been trying for hours to edit a file....  grrrrrr

---

### Post by artistic on 2006-07-17
In order to edit xorg.conf as root, do a:
sudo gedit /etc/X11/xorg.conf
That will prompt you for your password, and then let you edit / save the xorg.conf file.
I recommend that you backup xorg.conf before doing any editing, simply doing a: sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
This way you can always copy the xorg.conf.backup file back as xorg.conf, if you mess up your screen.

---

