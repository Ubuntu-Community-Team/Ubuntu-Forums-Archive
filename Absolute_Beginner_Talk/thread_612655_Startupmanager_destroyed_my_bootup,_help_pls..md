---
title: "Startupmanager destroyed my bootup, help pls."
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by dnns123 on 2007-11-14
I used startupmanager and set my resolution to 1024x768 and the bit to 16.
I rebooted and my comp wont boot up anymore. Can anyone help? I'm using the fiesty CD as a temporary OS right now :(.

---

### Post by overdrank on 2007-11-14
> **dnns123 said:**
> I used startupmanager and set my resolution to 1024x768 and the bit to 16.
I rebooted and my comp wont boot up anymore. Can anyone help? I'm using the fiesty CD as a temporary OS right now :(.

HI and can you boot in recovery mode, usually the second choice on the grub menu. TO correct the resolution in SUM.

---

### Post by philinux on 2007-11-14
Hopefully you have a backup of xorg.conf , that you can use.

---

### Post by dnns123 on 2007-11-14
Uhm, I cant get to the grub menu for some reason.

And I dont have a copy of my xorg..... :(( I didnt think that what I did was this devastating....

---

### Post by philinux on 2007-11-14
From the live cd using gksudo nautilus browse to 

/etc/X11/ there should be a file there called /etc/X11/xorg.conf~

Hopefully this is the backup file, check it's date stamp.

---

### Post by overdrank on 2007-11-14
> **philinux said:**
> From the live cd using gksudo nautilus browse to 

/etc/X11/ there should be a file there called /etc/X11/xorg.conf~

Hopefully this is the backup file, check it's date stamp.

Hi and please correct me if I am wrong but SUM changes the resolution in the grub list not the xorg.

---

### Post by dnns123 on 2007-11-14
Uhm, the xorg.conf is here, but how do I undo what I did in startup manager?

What does Startup manager adjust anyway? maybe I can see it (hopefully)

---

### Post by bulldog on 2007-11-14
If SUM did change your menu.lst,you are looking at the wrong file.
You need the /boot/grub/menu.lst to look for.

But I have no idea what SUM is nor what it does.:(

---

### Post by dnns123 on 2007-11-14
ugh.... i dont want to download my whole updates and other stuff, and spend 2 hours configuring everything.......

---

### Post by overdrank on 2007-11-14
> **dnns123 said:**
> ugh.... i dont want to download my whole updates and other stuff, and spend 2 hours configuring everything.......

Hi and you may find some help here
[http://ubuntuforums.org/showthread.php?t=295524](http://ubuntuforums.org/showthread.php?t=295524)

---

### Post by philinux on 2007-11-14
Overdrank - my bad, had a bad nights sleep.

I've ran SUM to correct my usplash and all it did was append this vga bit to grub

```
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9024104a-fa2f-4f85-bb6d-385637bdee48 ro quiet splash **[COLOR="Red"]vga=773[/COLOR]**
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```

Maybe the OP needs to 
remove that from his menu.lst

---

### Post by dnns123 on 2007-11-14
uhm, I dont think thats the problem.... I just changed the resolution in the SUM and the bit to 16. In the menu.lst, i cant find anything that written with 1024x768 or anything similar. my vga is 791 BTW.

---

### Post by bulldog on 2007-11-14
Can you post your whole menu.lst please?
maybe you over looked something.

---

### Post by dnns123 on 2007-11-14
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		1

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=cf57ea81-c654-4472-a22a-e6130c8ab785 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=791

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=cf57ea81-c654-4472-a22a-e6130c8ab785 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=cf57ea81-c654-4472-a22a-e6130c8ab785 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by dnns123 on 2007-11-14
lolz, the smileys are on... hahaha

---

### Post by philinux on 2007-11-14
also post /etc/X11/xorg.conf

---

### Post by dnns123 on 2007-11-14
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
	Identifier	"nVidia Corporation G80 [GeForce 8800 GTS]"
	Boardname	"NVIDIA GeForce 8 Series"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"MAG Technology Co., Ltd."
	Modelname	"MAG 986PF"
	Horizsync	30.0-86.0
	Vertrefresh	50.0-160.0
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
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8800 GTS]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1856	1392
		Modes		"1024x768@43"	"1152x864@75"	"1024x768@60"	"1280x1024@75"	"1024x768@70"	"1280x960@60"	"1024x768@75"	"1280x960@85"	"1024x768@85"	"1280x1024@60"	"832x624@75"	"1280x960@75"	"800x600@60"	"1400x1050@60"	"800x600@85"	"1400x1050@75"	"800x600@75"	"1600x1200@65"	"800x600@72"	"1600x1200@60"	"800x600@56"	"1792x1344@60"	"640x480@85"	"1856x1392@60"	"640x480@75"	"640x480@72"	"640x480@60"
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

---

### Post by philinux on 2007-11-14
I remember now SUM did this to my xorg.conf

you need to restore it from the backup or do the reconfigure xorg thing.

It didn't stop me booting though just messed up my desktop

---

### Post by ByteJuggler on 2007-11-14
> **philinux said:**
> From the live cd using gksudo nautilus browse to 

/etc/X11/ there should be a file there called /etc/X11/xorg.conf~

Hopefully this is the backup file, check it's date stamp.

Surely this will not be /etc/X11/xorg.conf~ if booted from the LiveCD?  It will be something like

/media/hda1/etc/X11/xorg.conf~ 

To the original poster: Post the output of the "sudo fdisk -lu" command please.

---

### Post by dnns123 on 2007-11-14
Im not familiar with xorg.... wheres the back up? Or was that supposed to be manually done by me? If so, "oh god...."

I really feel this can easily be fixed by editing a few lines of something.... :(

---

### Post by bulldog on 2007-11-14
Did you use the vga=791 option from the start,or did SUM put it there?
Basically you can remove this option to see if anything is changing [two places it's listed]
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=791
```
```
title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=cf57ea81-c654-4472-a22a-e6130c8ab785 ro quiet splash vga=791
initrd /boot/initrd.img-2.6.22-14-generic
quiet
```

```
sudo update-grub
```
Can be usefull too.

---

### Post by philinux on 2007-11-14
bytejuggler, the OP has enough intelligence to find his xorg.conf as he clearly demonstrated by posting it's contents.

---

### Post by dnns123 on 2007-11-14
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   190739744    95369841    5  Extended
/dev/sda2   *   190739745   234436544    21848400   83  Linux
/dev/sda5             189   188747684    94373748    7  HPFS/NTFS
/dev/sda6       188747748   190739744      995998+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by dnns123 on 2007-11-14
@ Bulldog

I edited the menu.lst when I first installed my 64bit Ubuntu. I did the vga = 791 and deleted the "quiet" part.

---

### Post by dnns123 on 2007-11-14
ok, thanks guys for trying. I fixed it. Heres what I did:

Before getting problems, my grub timeout was just 1 second. (to lessen bootup time, but still with safety in mind.)

With all the problems above, I went to my menu.lst and edited it to 3 seconds.

I saw the grubbootloader and saw the "ESC" option which Ive forgotten all about. ( cant see it with a 1 sec timeout)

So I chose the 2nd option in the list and it started in CLI. I type "startx" and the desktop started.

I got to open the Startup Manager and reverted everything back to the original.

Rebooted and seems like nothing happened.




Problems like this keeps me hooked to Linux. If it aint broken, it aint tweaked enough... haha

---

### Post by philinux on 2007-11-14
In that case just have peek at xorg.conf and see what its like now. I bet it hasn't got all those multiple entries for screen resolution etc.

---

### Post by ByteJuggler on 2007-11-14
> **philinux said:**
> bytejuggler, the OP has enough intelligence to find his xorg.conf as he clearly demonstrated by posting it's contents.

Dude...

I didn't imply anything about the OP, I was addressing **_you_**, and pointing out that **as stated**, **_your _**instructions would look in/on/at the **_[U]Live CD's root filesystem xorg.conf_[/U]**, not the one on his HDD.  Which I think you'll agree is not really all that helpful when you're trying to restore the previous version of the xorg.conf~ file (which of course wouldn't be located on the LiveCD's root filesystem.)  The fact that he posted "a" xorg.conf file doesn't after all mean that it was the one from his installation now does it?

Edit: Glad to see the OP got it fixed anyway. :)

---

### Post by Jimmy_r on 2007-12-15
> **philinux said:**
> I remember now SUM did this to my xorg.conf

you need to restore it from the backup or do the reconfigure xorg thing.

It didn't stop me booting though just messed up my desktop

That is interesting. I wrote SUM, and none of those ~2000 lines of code has any reference to xorg.conf whatsoever.
Perhaps you are thinking of a different tool such as displayconfig-gtk?

---

### Post by philinux on 2007-12-15
No honestly thats what happened.

I had out of range on startup and shutdown everything else worked fine. Used startup manager once and it fixed the splash screens but i ended up with xorg.conf messed up and had to restore the backup.

---

### Post by Jimmy_r on 2007-12-18
You mean you ran SUM, and it made your xorg.conf look like the one posted by dnns123, with all the funky modelines and stuff?
I know displayconfig-gtk does it(System -> Administration -> Screens and Graphics).

If I was to estimate the chance SUM added those modelines and stuff to xorg.conf... Well, have you heard of that hurricane passing through a scrap yard and assembling a jumbojet? That is kind of close.

SUM touching xorg.conf at all? Well, about the chance of an elephant crashing through your livingroom wall. :)

Feel free to try and reproduce it though. If that bug really exist, it might make me very famous :)

---

