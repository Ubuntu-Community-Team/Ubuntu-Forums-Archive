---
title: "Dual booting Ubuntu (Breezy) and Windows XP"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by ubunTux on 2006-10-23
Greetings everyone!

I recently tried dual booting Windows XP Pro and Ubuntu Breezy. I installed Windows XP first, then installed Ubuntu Breezy afterwards. I installed both platforms on a single physical hard drive. After installing and booting Ubuntu, I noticed that Windows XP wasn't on my GRUB Menu list. I am aware that Ubuntu installation will detect my existing Windows XP and must've added this to the GRUB menu. Unfortunately, it wasn't in my list.

During Ubuntu installation, I chose to manually set up the partition and made the mount point /boot to bootable.

What I did is added Windows XP to /boot/grub/menu.lst and here is what it looks like now:
> 
# menu.lst - See: grub( 8 ), info grub, update-grub( 8 )
#            grub-install( 8 ), grub-floppy( 8 ),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		30

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda4 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,2)
kernel		/vmlinuz-2.6.12-10-386 root=/dev/hda4 ro quiet splash
initrd		/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.12-10-386 root=/dev/hda4 ro single
initrd		/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,2)
kernel		/vmlinuz-2.6.12-9-386 root=/dev/hda4 ro quiet splash
initrd		/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.12-9-386 root=/dev/hda4 ro single
initrd		/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/memtest86+.bin  
boot

title		Windows XP Professional
root		(hd0,0)
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST


The problem is, whenever I choose Windows XP Professional from the list, it gives me the following error:
> 
Booting "Windows XP Professional"
root (hd0,0)
Filesystem type unknown, partition type 0xf.


**What could have been the problem?**


For more supporting infos, here's what **fdisk -l** gives me:
> 
Disk /dev/hda: 40.8 GB, 40822161408 bytes
255 heads, 63 sectors/track, 4963 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2        1958    15719602+   f  W95 Ext'd (LBA)
/dev/hda2   *        1959        2020      498015   82  Linux swap / Solaris
/dev/hda3            2021        2035      120487+  83  Linux
/dev/hda4            2036        4963    23519160   83  Linux
/dev/hda5               2        1958    15719571    7  HPFS/NTFS


and **cat /boot/grub/device.map** gives me this:
> (hd0)   /dev/hda

Any help would be greatly appreciated...



.ubuntux

---

### Post by Episteme on 2006-10-23
From what I've read, try editing your menu.1st from this...

title Windows XP Professional
root (hd0,0)
makeactive
chainloader +1

to this...

title Microsoft Windows XP Professional 
rootnoverify (hd0,0) 
savedefault 
makeactive 
chainloader +1

---

### Post by grim918 on 2006-10-23
Try changing the zero on your root(hd0,0) to a four. I provided an example of how it should look like. hd0 is the device and the other number is the partition. 0 is the first partition and so on, therefore, 4 would be your windows partition. It should work, I haven't played around with grub in a while.
```

title Windows XP Professional
root (hd0,4)
makeactive
chainloader +1

```

---

