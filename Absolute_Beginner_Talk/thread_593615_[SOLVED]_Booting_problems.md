---
title: "[SOLVED] Booting problems"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by The_Shady_1 on 2007-10-27
I'm trying to dual with 2 HDD's, WinXp on SATA and Ubuntu 7.10 on IDE. I unplugged the SATA when I installed Ubuntu. I found out how to boot between the two by going inot my BIOS and selecting which one should boot first. However, when I boot this way it messes up my BIOS, time and date for the other OS. Is there a way to have some sort of promt to ask if I want to boot WinXp or Ubuntu without having to go through the BIOS all the time?

---

### Post by Pumalite on 2007-10-27
Post: 
sudo fdisk -lu (both drives connected)
cat /boot/grub/menu.lst

---

### Post by sad_iq on 2007-10-27
Read these 2 guides here...they helped me:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dual+boot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dual+boot) 
[http://ubuntuforums.org/showthread.php?t=275728&highlight=dual+boot](http://ubuntuforums.org/showthread.php?t=275728&highlight=dual+boot)

---

### Post by The_Shady_1 on 2007-10-27
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x32f932f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   976768064   488384001    7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe40be40b

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    74862899    37431418+  83  Linux
/dev/hdb2        74862900    78156224     1646662+   5  Extended
/dev/hdb5        74862963    78156224     1646631   82  Linux swap / Solaris



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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=342ae052-7f56-47db-8cc1-df813e5cc6ec ro

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=342ae052-7f56-47db-8cc1-df813e5cc6ec ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=342ae052-7f56-47db-8cc1-df813e5cc6ec ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Steve1961 on 2007-10-27
Try adding this entry to menu.lst

title           Microsoft Windows XP
root            (hd0,0)
savedefault
chainloader     +1

---

### Post by Pumalite on 2007-10-27
I don-t see any way to correct your Grub. You installed that way. You-ll have to live with it. (that is, changing order in BIOS)

---

### Post by The_Shady_1 on 2007-10-27
> **Steve1961 said:**
> Try adding this entry to menu.lst

title           Microsoft Windows XP
root            (hd0,0)
savedefault
chainloader     +1

How do I do that ?

---

### Post by Steve1961 on 2007-10-27
Actually ignore those last instructions.  Grub is already pointing to the first hard drive partition - not sure if you can change this because of the way you've installed

---

### Post by The_Shady_1 on 2007-10-27
So the only way to fix would be to reformat and reinstall ?

---

### Post by Steve1961 on 2007-10-27
Unless anyone has any other suggestions, if it were me I'd probably just reinstall and let grub write to the mbr

---

### Post by The_Shady_1 on 2007-10-27
So if I reinstall and let it write to mbr it will prompt me for OS selection ? I am somewhat worried about messing up the XP partition, although I do have my XP OEM installation cd on hand.

---

### Post by Steve1961 on 2007-10-27
If you set the xp disk as the first drive before installing ubuntu you should be fine.  Ubuntu should pick up the windows installation and add an entry to the grub menu.  It 'shouldn't' mess up the xp partition, but always backup your files beforehand.

---

### Post by meierfra on 2007-10-27
You shouldn't  have to reinstall. There are various  options still available

Try this first:

Set your bios to  boot from the ide  drive.

open the file /boot/grub/menu.lst via
```
gksudo gedit /boot/grub/menu.lst
```
Look for:

> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

change "hiddenmenu" to  "#hiddenmenu"

This will give you the "grub menu" at boot up.

Add this to the end of the file:

title Microsoft Windows XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

This  adds "windows" to you grub menu and you should be able to boot into ubuntu and windows from the grub menu.

---

### Post by sad_iq on 2007-10-27
Actually DO what Steve1961 said you to write and just put the bios to boot from your ubuntu disk. To do that type: ```
gksudo gedit /boot/grub/menu.lst
```
 then before ###BEGIN AUTOMAGIC KERNEL LIST paste this: ```
 
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

 Darn...meierfra beat me to it...he is also right...any methot should work

---

### Post by The_Shady_1 on 2007-10-27
I did see a prompt from OS selection this time, went by a bit quick but I did see it. Heres what I have from meierfra's directions :

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
timeout		3

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
# kopt=root=UUID=342ae052-7f56-47db-8cc1-df813e5cc6ec ro

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
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=342ae052-7f56-47db-8cc1-df813e5cc6ec ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=342ae052-7f56-47db-8cc1-df813e5cc6ec ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title Microsoft Windows XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1



### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by meierfra on 2007-10-27
change "timeout 3" to  "timeout 10" in menu.lst  to give yourself more time. At the grub menu at boot up use the arrow keys to select an item. Then press enter.

---

### Post by sad_iq on 2007-10-27
Try to change this **timeout 3** to something bigger...3 is the seconds you have to wait for the main OS to boot, also delete the # in front of #hiddenmenu, then when you boot scroll down and select windows...and do tell us if it works!!!

---

### Post by The_Shady_1 on 2007-10-27
It worked ! :) I changed the timeout to 30. When I removed the # from hiddenmenu it became a countdown to load grub rather than when I left it there it displayed the OS selection menu right away. A BIG thank you to all that helped. This was much easier than having to do a reinstall.

---

