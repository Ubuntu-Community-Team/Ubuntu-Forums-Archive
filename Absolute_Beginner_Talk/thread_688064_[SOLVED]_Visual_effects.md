---
title: "[SOLVED] Visual effects?"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by myddewji13 on 2008-02-05
Hi, 
I cant seem to get the visual effects up and running on my laptop... some help please (could not figure out on my own from prev posts)

---

### Post by zabien1970 on 2008-02-05
Could you provide more info, like what version of ubuntu you are using, what you have done so far

---

### Post by oedha on 2008-02-05
what is your display adapter ?
what version of ubuntu you have ?
have you enable the desktop effect ? 
( right click on desktop - change desktop background - visual effect - extra )

---

### Post by myddewji13 on 2008-02-05
have done nothing except try to enable via the preference -appearance menu..

---

### Post by myddewji13 on 2008-02-05
and using 7.10

---

### Post by myddewji13 on 2008-02-05
i dont noe how to find my display adaptor...anything i try doesnt let me enable ...so some help would be greatly appreciated...sorry for the split up posts...still getting used to this forum

---

### Post by oedha on 2008-02-05
what is your laptop ?

---

### Post by jordanmthomas on 2008-02-05
> **myddewji13 said:**
> i dont noe how to find my display adaptor...anything i try doesnt let me enable ...so some help would be greatly appreciated...sorry for the split up posts...still getting used to this forum

```
sudo lshw -short
``` Can you post this?  It will tell us what kind of graphics card you have (among other things, but I'm not at a linux box right now so I don't know which -class to use to get just the graphics card)

---

### Post by oedha on 2008-02-05
sudo lshw -short -class display

---

### Post by myddewji13 on 2008-02-05
this is what i get :
H/W path             Device      Class       Description
========================================================
                                 system      HP Pavilion dv2700 Notebook PC
/0                               bus         30CD
/0/0                             memory      102KB BIOS
/0/4                             processor   Intel(R) Pentium(R) Dual  CPU  T233
/0/4/5                           memory      64KB L1 cache
/0/4/6                           memory      1MB L2 cache
/0/4/1.1                         processor   Logical CPU
/0/4/1.2                         processor   Logical CPU
/0/f                             memory      2GB System Memory
/0/f/0                           memory      1GB SODIMM Synchronous 533 MHz (1.9
/0/f/1                           memory      1GB SODIMM Synchronous 533 MHz (1.9
/0/100                           bridge      Mobile PM965/GM965/GL960 Memory Con
/0/100/2                         display     Mobile GM965/GL960 Integrated Graph
/0/100/2.1                       display     Mobile GM965/GL960 Integrated Graph
/0/100/1a                        bus         82801H (ICH8 Family) USB UHCI Conto
/0/100/1a.1                      bus         82801H (ICH8 Family) USB UHCI Contr
/0/100/1a.7                      bus         82801H (ICH8 Family) USB2 EHCI Cont
/0/100/1b                        multimedia  82801H (ICH8 Family) HD Audio Contr
/0/100/1c                        bridge      82801H (ICH8 Family) PCI Express Po
/0/100/1c.1                      bridge      82801H (ICH8 Family) PCI Express Po
/0/100/1c.1/0        eth0        network     88E8039 PCI-E Fast Ethernet Control
/0/100/1c.2                      bridge      82801H (ICH8 Family) PCI Express Po
/0/100/1c.3                      bridge      82801H (ICH8 Family) PCI Express Po
/0/100/1c.3/0                    network     BCM4310 USB Controller
/0/100/1d                        bus         82801H (ICH8 Family) USB UHCI Contr
/0/100/1d.1                      bus         82801H (ICH8 Family) USB UHCI Contr
/0/100/1d.2                      bus         82801H (ICH8 Family) USB UHCI Contr
/0/100/1d.7                      bus         82801H (ICH8 Family) USB2 EHCI Cont
/0/100/1e                        bridge      82801 Mobile PCI Bridge
/0/100/1e/9                      bus         R5C832 IEEE 1394 Controller
/0/100/1e/9.1                    system      R5C822 SD/SDIO/MMC/MS/MSPro Host Ad
/0/100/1e/9.2                    system      R5C843 MMC Host Controller
/0/100/1e/9.3                    system      R5C592 Memory Stick Bus Host Adapte
/0/100/1e/9.4                    system      xD-Picture Card Controller
/0/100/1f                        bridge      82801HEM (ICH8M) LPC Interface Cont
/0/100/1f.1          scsi0       storage     82801HBM/HEM (ICH8M/ICH8M-E) IDE Co
/0/100/1f.1/0.0.0    /dev/cdrom  disk        DVD A  DS8A1H
/0/100/1f.1/0.0.0/0  /dev/cdrom  disk        
/0/100/1f.2          scsi2       storage     82801HBM/HEM (ICH8M/ICH8M-E) SATA A
/0/100/1f.2/0.0.0    /dev/sda    disk        232GB FUJITSU MHY2250B
/0/100/1f.2/0.0.0/1  /dev/sda1   volume      148GB HPFS/NTFS partition
/0/100/1f.2/0.0.0/2  /dev/sda2   volume      11GB HPFS/NTFS partition
/0/100/1f.2/0.0.0/3  /dev/sda3   volume      1906MB Linux swap / Solaris partiti
/0/100/1f.2/0.0.0/4  /dev/sda4   volume      71GB Linux filesystem partition
/0/100/1f.3                      bus         82801H (ICH8 Family) SMBus Controll
/1                               power       Intel Corporation

---

### Post by jordanmthomas on 2008-02-05
> [0/100/2 display Mobile GM965/GL960 Integrated Graph
You seem to have an integrated Intel chip.  This is surprising, because this card should work with desktop effects (and work pretty well, I might add) out of the box.

What is in your /etc/X11/xorg.conf?

---

### Post by myddewji13 on 2008-02-05
my what?....no idea what you are talking about

---

### Post by jordanmthomas on 2008-02-05
Sorry, 
```
gedit /etc/X11/xorg.conf
```
Copy and paste that in here (preferrably put it in [code] tags to make it easier to read)

xorg.conf holds the options for your graphics system.  If compiz doesn't work, it's usually because of something in this file.

---

### Post by myddewji13 on 2008-02-05
ok this is what i get

> [QUOTE]# xorg.conf (xorg X Window System server configuration file)
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800" "1136x67" "304x256"
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
	InputDevice	"Synaptics Touchpad"
EndSection[/QUOTE]

---

### Post by jordanmthomas on 2008-02-05
OK, I see something that's missing that compiz requires I think.
Close gedit.  We need to edit the file and so we'll need to use sudo since it's a system file.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup  [COLOR="Red"]#make a backup just in case[/COLOR]
gksudo gedit /etc/X11/xorg.conf
```
And add this at the very bottom:
```
Section "Extensions"
        Option "Composite" "Enable"
EndSection

```
Save the file and close gedit.
Log out and back in, and you *should* be able to enable desktop effects.

---

### Post by myddewji13 on 2008-02-05
still no luck...i restarted..and i get the same message 'could not be enabled'

---

### Post by jordanmthomas on 2008-02-05
Hm, I am not sure what's wrong then.
does ```
compiz --replace
``` work?
It's a shot in the dark, but at least this will tell you WHY compiz won't start.

---

### Post by myddewji13 on 2008-02-05
this is what i get

```
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity
```

---

### Post by jordanmthomas on 2008-02-05
AHA! 
[http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

Your card is blacklisted.
You can run it if you run compiz like this:
```
SKIP_CHECKS=yes compiz --replace
```
If this works you can set up a more permanent solution.

---

### Post by myddewji13 on 2008-02-05
didnt work...now what?

---

### Post by myddewji13 on 2008-02-05
ok...something worked...and th
en reset... back to not working :( 

anyway this is what it showed me:
```

Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

---

### Post by myddewji13 on 2008-02-05
YEA!!!!!

ok...if i type in:

```
SKIP_CHECKS=yes compiz
```

it works!!!!

now how do i make this permenant?

---

### Post by myddewji13 on 2008-02-05
ALRIGHT!!!
FIGURED IT  YEA!!

anyway this is how i did it:

```
sudo gedit ~/.config/compiz/compiz-manager
```

and then paste in the line

```
SKIP_CHECKS=yes
```

and the reboot for good measire ... tada :P

---

### Post by jordanmthomas on 2008-02-05
sorry I didn't reply earlier, was off browsing the web.
Glad you got it sorted out.

One thing though, you never need to use sudo to launch gedit:  use gksudo instead.  Also, to edit that particular file you could have just used gedit ~/.config/compiz/compiz-manager since that file is owned by your own user. 

It probably didn't do any harm, but if you use sudo when you don't need to it can lead to permission problems later on.

---

### Post by Roko84 on 2008-02-05
hello.

it is posible to make transparent windows in ubuntu?

---

### Post by jordanmthomas on 2008-02-05
> **Roko84 said:**
> hello.

it is posible to make transparent windows in ubuntu?

Yes, if you have compiz running (desktop effects) just hold down the alt button and use your mouse's scroll wheel to adjust transparency.

If you don't, you can still look up xcompmgr and transset.  Combined, they will give you transparent windows.  Also, you could look into kwin or xfwm which have built-in compositors you can use.

---

