---
title: "error 12: invalid device requested"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by GnuUser on 2007-06-08
Hey everyone, I installed Feisty Fawn 64 bit edition a few weeks ago, then I had to format and reinstall my windows xp install (deleted partition AND created to new partitions) windows install went great, then I had to reconfig grub (I followed directions from someones online howto load grub after reinstalling windows) now when  I try choosing windows partition from grub i get "error 12: invalid deice requested. Press any key to continue"

P.S. anyone know how to get shockwave content to play in firefox?

---

### Post by GnuUser on 2007-06-08
If this helps at all heres my -l fdisk & menu.lst

mendy@mendy-desktop:~$ sudo fdisk -l

Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2       15936   127997887+   f  W95 Ext'd (LBA)
/dev/hda2           15937       28337    99611032+  83  Linux
/dev/hda3           28338       28586     2000092+  82  Linux swap / Solaris
/dev/hda4   *       28587       31136    20482875    7  HPFS/NTFS
/dev/hda5               2       15936   127997856    7  HPFS/NTFS
mendy@mendy-desktop:~$ 




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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

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
# kopt=root=UUID=246d2ef4-569b-4025-a49b-7118dc559f99 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=246d2ef4-569b-4025-a49b-7118dc559f99 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=246d2ef4-569b-4025-a49b-7118dc559f99 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=246d2ef4-569b-4025-a49b-7118dc559f99 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=246d2ef4-569b-4025-a49b-7118dc559f99 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by yuanfangcan on 2007-06-08
change to 

title Microsoft Windows XP Professional
root (hd0,[COLOR="Red"]4[/COLOR])
savedefault
makeactive
chainloader +1


and see what happen

---

### Post by GnuUser on 2007-06-09
Yeah I had tried that originally, what Actually worked though was (hd0,3) the linux os gets confusing with first drive being 0, second 1 etc...

---

### Post by Golgo on 2007-06-10
Hi, I have a similar problem but it seems mine is slightly worse.
I had Vista installed before I installed Ubuntu. I created a separate partition for Ubunto and added some swap space.
Now grub wont find Vista although its there and I know its not overwritten. I have tried to set the Vista option i grub from (hd0,0) to (hd0,6).   

My menu.lst:

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=cc5e454d-0bfe-46a4-aa72-e836719d2348 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cc5e454d-0bfe-46a4-aa72-e836719d2348 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cc5e454d-0bfe-46a4-aa72-e836719d2348 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

and fdisk -l:
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    f  W95 Ext'd (LBA)
/dev/sda5            5100       30401   203238283+   7  HPFS/NTFS
/dev/sda6               1        4972    39937495+  83  Linux
/dev/sda7            4973        5099     1020096   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 262 MB, 262144000 bytes
255 heads, 63 sectors/track, 31 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          32      255968+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(30, 254, 63) logical=(31, 221, 62)

---

### Post by Golgo on 2007-06-10
bump
please, a little help here

---

### Post by confused57 on 2007-06-10
> **Golgo said:**
> bump
please, a little help here
Try root (hd0,4):
```
title Windows Vista
root (hd0,4)
savedefault
makeactive
chainloader +1
```

Also, you need to place your Window's entry at the very end of the menu.lst file, after the ###END DEBIAN AUTOMATIC KERNELS LIST...a kernel update will remove the Window's entry where you have it now.

Did you resize your Vista partition with the Ubuntu partitioner?  If you didn't, your Vista should boot OK.

---

### Post by Golgo on 2007-06-10
I get the same error (Error 12), and no, i didn't touch my Vista partition pre install.

---

### Post by confused57 on 2007-06-10
Here's some info & possible solutions for grub error 12:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#12_](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#12_)

---

### Post by britoca on 2008-04-02
> **confused57 said:**
> Here's some info & possible solutions for grub error 12:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#12_](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#12_)

I'm also having some trouble with this issue and I'm just pasting the updated grub error 12 link:

[http://users.bigpond.net.au/hermanzone/p15.htm#12_](http://users.bigpond.net.au/hermanzone/p15.htm#12_)

---

### Post by perham on 2008-06-04
remove the makeactive line from Grub entry. make the partition bootable in Gparted by setting boot flag. boot into M$ Winblows! :D

---

