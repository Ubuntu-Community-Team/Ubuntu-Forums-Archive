---
title: "Dual boot not appearing"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by reesy on 2008-01-24
I have just installed Xp back on my home pc and now I don't get the dual boot option for my Ubuntu Gutsy Gibbon or Ubuntu Studio when i boot the computer. Instead it just autmaticlly logs into Xp without giving me the option to choose which one I want to boot into like before. If any one could explain to  me how to get around this I would be very grateful as I don't want to be stuck on Xp. Thanks.

---

### Post by Arwen on 2008-01-24
That's normal,XP's bootloader deletes any other bootloader when you install it after linux,so now you have to reinstall grub.Take a look at [this]("http://ubuntuforums.org/showthread.php?t=224351") while waiting for someone more experienced to give you the exact commands if you want.

---

### Post by seventhc on 2008-01-24
When doing multiple boot setup it is always best to install windows first and ubuntu last. Then you will get your boot options right away with nothing to configure.

---

### Post by philinux on 2008-01-24
> **Arwen said:**
> That's normal,XP's bootloader deletes any other bootloader when you install it after linux,so now you have to reinstall grub.Take a look at [this]("http://ubuntuforums.org/showthread.php?t=224351") while waiting for someone more experienced to give you the exact commands if you want.

That link is the way to go. Windoze has overwritten your mbr with its own bootloader so grub has gone.

---

### Post by reesy on 2008-01-24
Rite I did as it said in the other thread but now my Xp partition isn't appearing. How do I get it to appear in the dual boot? oh and thanks for the help I've had so far.

---

### Post by logos34 on 2008-01-24
> **reesy said:**
> Rite I did as it said in the other thread but now my Xp partition isn't appearing. How do I get it to appear in the dual boot? oh and thanks for the help I've had so far.

You need to add windows to menu.lst:

gksudo gedit /boot/grub/menu.lst

Use the example at the top as a guide:

>  examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1


Put it at the very bottom without hashes #.  Ex.: if your win partition is, say, sda3, then:

> title		Windows 95/98/NT/2000
**root		(hd0,2)**
makeactive
chainloader	+1

---

### Post by Gambini on 2008-01-24
To add on to what logos said about the menu.lst, type this in to a terminal from a live CD of some sort:
```
fdisk -l
``` (that's a lower case "L", and you might need a sudo in front)

And take the NTFS partition (sdax, where x is the number of your NTFS partition) and put that x minus one for the root. For instance, mine was on sda3, so next to "root" I put "(hd0,2)". If it is on another HDD, like hdb1, you would have "(hd1,0)", and so on and so forth. That tricked me for a while, so I thought that I would point it out.

---

### Post by reesy on 2008-01-25
I check what partition my Xp was by looking for the NTFS drive and this is what came up> :
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001a843

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9727    78132096   83  Linux
/dev/sda2            9728       14749    40339215   83  Linux
/dev/sda3   *       14750       18892    33278647+   7  HPFS/NTFS
/dev/sda4           18893       19457     4538362+   5  Extended
/dev/sda5           18893       19457     4538331   82  Linux swap / Solaris


It shows that it's sda3 so i subtracted 1 giving me two. I then pasted 

> title Windows 95/98/NT/2000
root (hd0,2)
makeactive
chainloader +1

into the 'menu.lst' and nothing happened. I've tried pasting it in different places in the file a few times now and not once have I been able to boot into Xp or has it even showed up on the list. Here's a copy of the whole '/boot/grub/menu.lst' before I edited it. If someone could please edit it and post it back for me I would be grateful.

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
timeout		3

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
# kopt=root=UUID=c136f0c9-f2a5-4819-ae57-438eaa5fd0a7 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c136f0c9-f2a5-4819-ae57-438eaa5fd0a7 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c136f0c9-f2a5-4819-ae57-438eaa5fd0a7 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by smurphy_it on 2008-01-25
# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=c136f0c9-f2a5-4819-ae57-438eaa5fd0a7 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##
title Windows XP/Vista
root (hd0,2)
makeactive
chainloader +1

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=c136f0c9-f2a5-4819-ae57-438eaa5fd0a7 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=c136f0c9-f2a5-4819-ae57-438eaa5fd0a7 ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by reesy on 2008-01-25
I pasted that into the file and it still doesn't work. Could any one confirm that the code above is correct and if it is suggest another way of getting my Xp partition to appear please. Thanks.

---

### Post by seventhc on 2008-01-25
Your timeout for the menu is set to 3 seconds are you sure that maybe it's not just loading ubuntu to fast and maybe your missing the menu?
also for the boot selection for your xp partition if you try it with 1 or 3 it is safe to do so as long as you don't change the ubuntu part.. Your xp shows an (*) next to it, I think thats a bootable partition. I would try it with 3, if that didn't work I'd try it with 1. the worst thing that can happen is that it will boot into ubuntu, so don't be afraid, just be careful. Don't change anything in the ubuntu part.

---

### Post by reesy on 2008-01-25
Still no luck.

---

### Post by logos34 on 2008-01-25
Are you pressing Esc key to bring up the grub menu screen?  Because even if you increase the timeout you've still got 'hiddenmenu' enabled.  Disable it:

> [COLOR="Red"]#[/COLOR]hiddenmenu

I don't see where you pasted the windows stanza in menu.lst.  Should be at the bottom, **below** the line 
### END DEBIAN AUTOMAGIC KERNELS LIST

(DOn't put it in the automagic section with the ubuntu kernels like smurphy posted--it'll be evicted next kernel update)

XP is flagged boot (*), so that's not the problem.

(hd0,2) is correct.

---

### Post by seventhc on 2008-01-25
OK I think maybe I see the problem
title Microsoft Windows XP Professional
**root (hd0,2)**
savedefault
makeactive
chainloader +1


also look at this thread..[http://ubuntuforums.org/showthread.php?t=642648](http://ubuntuforums.org/showthread.php?t=642648)..where I saw the menu. You also might need to put this entry after the ubuntu entry not in front of it.
actually your settings would prob work if you move to so it's after ubuntu too. read that thread though it's not long, just the first page. :)

---

