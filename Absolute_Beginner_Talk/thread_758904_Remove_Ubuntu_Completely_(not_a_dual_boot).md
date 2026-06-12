---
title: "Remove Ubuntu Completely (not a dual boot)"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by gymophett on 2008-04-18
Ok. All I have is Ubuntu only on my computer. I dont have a windows xp disk (all the threads say to use the xp disk to do so and so.) All I want to do is remove Ubuntu completely leaving the harddrive. Im extremely new to ubuntu so please dont tell me bunches of high tech things that I dont know. All I want to do is completely uninstall Ubuntu. Thats it.

Sorry for repeating myself but no one ever understands.
Thank You All:)

Help?!

---

### Post by forceofnature on 2008-04-18
Load the live CD and run gparted un dr the system tools then you click the partition with linux.  press delete Key.  Now you have a big unallocated drive.  Now you will right click and create a new logical or boot drive and Select NTFS instead of the default of /ext.  Click apply then you have a blank disk formated and ready for XP.

---

### Post by DGortze380 on 2008-04-18
Boot from the ubuntu live cd by putting it in the drive and holding the "C" key at start-up.  Open a terminal and type:

```

sudo gparted

```

Select your "/" partition and click the delete button.
Select your "swap" partition and click the delete button.
Click Apply and wait.

Shutdown. 

You now have a blank(-ish) hard drive.  After you install windows most of your old data will be pretty far gone, but the only way to complete destroy your data is to destroy the drive.

---

### Post by gymophett on 2008-04-18
Thanks everyone :). I still havent tried yet, but Ill come back if anymore problems. :)

Thanks Again :)

---

### Post by NOLU on 2008-04-27
If I remove Ubuntu 8.04 by the above method, can I reinstall 7.10 and use the gap that is left by 8.04 or do I need to allocate the space to Windows first?

7.10 was fine for me but 8.04 is extremely slow from the internet to folders opening and scrolling even after turning off the effects.

I want to go back to what I had.

Thanks.

I am duel boot by the way.

---

### Post by nkuck on 2008-04-27
I think that I have the opposite problem. I installed Ubuntu on a Windows (Dell Latitude) machine and do not wish to select into which OS I want to boot every time I start up. So, can I change the order so that Ubuntu is the default? Can I/dare I totally remove Windows from this machine without sacrificing or affecting anything within Ubuntu? I am somewhat of a newbee with Windows (Mac for years!), so I proceed with caution. And then what do I do with it's partition?
Thanks for any help.

---

### Post by overdrank on 2008-04-27
> **nkuck said:**
> I think that I have the opposite problem. I installed Ubuntu on a Windows (Dell Latitude) machine and do not wish to select into which OS I want to boot every time I start up. So, can I change the order so that Ubuntu is the default? Can I/dare I totally remove Windows from this machine without sacrificing or affecting anything within Ubuntu? I am somewhat of a newbee with Windows (Mac for years!), so I proceed with caution. And then what do I do with it's partition?
Thanks for any help.

HI and you can make Ubuntu the default OS by editing the grub.ou can edit your grub menu with this command ```
gksudo gedit /boot/grub/menu.lst
```
Example
```
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
[COLOR="Blue"]default		0[/COLOR]

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=30c3f58c-f2f1-42b1-a239-54c5ae5cfba2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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
# defoptions=quiet splash

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

[COLOR="Red"]title	[/COLOR]	Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=30c3f58c-f2f1-42b1-a239-54c5ae5cfba2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=30c3f58c-f2f1-42b1-a239-54c5ae5cfba2 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu, kernel 2.6.20-16-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=f37fe8d7-11b8-4ae5-8158-5c967ab313c3 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=f37fe8d7-11b8-4ae5-8158-5c967ab313c3 ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu, kernel 2.6.20-15-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f37fe8d7-11b8-4ae5-8158-5c967ab313c3 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f37fe8d7-11b8-4ae5-8158-5c967ab313c3 ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

```
You well need to change the default from 0 ( highlighted in blue) to whatever you count of the title ( highlighted in red) and start with 0 when counting.
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)
If you do decide to delete the windows partition you can do this via the live cd using gparted. Then you can resize the Ubuntu partition or use it for data. Good luck!

---

