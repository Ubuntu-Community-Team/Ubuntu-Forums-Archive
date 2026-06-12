---
title: "adding windows to grub"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by ELD on 2007-12-27
Hi all i am trying to add windows into grub with some problems:

fdisk:
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000730bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321   83  Linux

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc4fcc4f

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        4865    39078081    7  HPFS/NTFS
/dev/hda2   *        4866        4927      498015   82  Linux swap / Solaris
/dev/hda3            4928        9729    38572065   83  Linux

```

So what do i need to add into grub?
Many thanks!

---

### Post by jas0 on 2007-12-27
Please provide us with the contents of the /boot/grub/device.map file.

---

### Post by ELD on 2007-12-27
Here it is buddy:

(hd0)	/dev/hda
(hd1)	/dev/sda
(hd2)	/dev/sdb

---

### Post by jas0 on 2007-12-27
Sorry, also could you paste your current /boot/grub/menu.lst?

Right now it seems like 

```
title         Windows
root          (hd0,0)
makeactive
#chainloader   +1
```

...should be the code to use, but I also noticed that you have your swap partition set as a bootable partition, so I just want to get more info.

---

### Post by ELD on 2007-12-27
Well i don't know why it is bootable, but it is not in grub? :S

---

### Post by jas0 on 2007-12-27
Try to compare the code I posted above with what you have in /boot/grub/menu.lst

Also, do paste your menu.lst here so that we have have a looksie. Also what is the boot priority of your drives in the BIOS?

---

### Post by ELD on 2007-12-27
The code you gave to boot windows doesnt work :(

Here is my menu with your addition:
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
# kopt=root=UUID=87590302-ec6f-4664-99fb-34389683abb8 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=87590302-ec6f-4664-99fb-34389683abb8 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=87590302-ec6f-4664-99fb-34389683abb8 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

title         Windows
root          (hd0,0)
makeactive
#chainloader   +1

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by jas0 on 2007-12-27
Hm... everything looks right to me. 

Do you have any issues booting into Ubuntu? What happens when you try to boot into Windows?

---

### Post by dstew on 2007-12-27
Remove the # from in front of the #chainloader +1 line in the Windows entry and try it again.

---

### Post by Tteddo on 2007-12-27
I have 2 machines like this and I had to remap the drives to get it to work as so:
> title		Windows 2000 Bork Bork
rootnoverify	(hd1,0)
makeactive
map		(hd0,0) (hd1,0)
map		(hd1,0) (hd0,0)
chainloader	+1

Of course changing it to match your HD's.

Just a tip, when you do get it working, you want to move your customizations below the line that says
> ### END DEBIAN AUTOMAGIC KERNELS LIST
Because when kernel updates come through what's between that line and the top one will get  modified and your changes will be lost.

---

### Post by meierfra on 2007-12-27
Follow dstew's advice and  Tteddo's second advice. So put this at  the very ** end** of menu.lst:


title         Windows
root          (hd0,0)
makeactive
chainloader   +1



Explanation: menu.lst contains "root (hd0,2)" for ubuntu. This means that ubuntu is the third partition on the first hard drive. (Grub starts counting at zero) Also for grub the  first hard drive is always the one you are booting from, not the one which appears first in "fdisk".  Since you can boot into ubuntu, the information from menu.lst must be correct. Looking at "fdisk" we see that  the only hard drive with  at least  three partitions is hda.  Hence  ubuntu is on hda, and  hda must be the first hard drive.  Looking at "fdisk" again we see that Windows is the first partition on hda.   So the Windows partition is the first partition on the first hard drive and grub will call it (hd0,0).

---

