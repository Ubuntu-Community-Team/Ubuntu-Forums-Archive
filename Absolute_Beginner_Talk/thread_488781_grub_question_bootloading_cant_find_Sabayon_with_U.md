---
title: "grub question/ bootloading: cant find Sabayon with Ubuntu"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by miesnerd on 2007-06-30
Ok, Im not exactly a noob in general, but when it comes to grub, I certainly am.
I installed Sabayon Linux first on a partition (hda4) and then Ubuntu next on to hda3. When loading grub, Ubuntu doesnt see Sabayon. I think the location of the bootloader is supposedly in 2 different locations. Sabayon said it installed it to hda1 (which I have marked as a boot partition) and Ubuntu put it in hda0. Regardless of that, without (preferably) having to reinstall, how do I get my Ubuntu bootloader to recognize that Sabayon is on hda4.

Thanks guys.

miesnerd

---

### Post by jimbob on 2007-06-30
Please post the output of fdisk -l and the contents of /boot/grub/menu.lst from the Ubuntu partition.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by miesnerd on 2007-06-30
sorry about that-- I guess I didnt think posting this would be necessary. I assumed you'd just give me some command to type into  grub> and all would be good. Thanks for this guys.

Disk /dev/hde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1         608     4883728+  83  Linux
/dev/hde2           30309       30401      747022+   5  Extended
/dev/hde3             766       16744   128351317+  83  Linux
/dev/hde4           16745       30308   108952830   83  Linux
/dev/hde5           30309       30401      746991   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdf: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1   *           1       10011    80413326   82  Linux swap / Solaris


and  then menu.lst


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
# kopt=root=UUID=a7c81681-f4da-470c-8af3-ed4222a17003 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a7c81681-f4da-470c-8af3-ed4222a17003 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a7c81681-f4da-470c-8af3-ed4222a17003 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hde1.
title		Ubuntu, kernel 2.6.20-16-generic (on /dev/hde1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=57829708-edc7-43d8-838f-8628d580f0d8 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hde1.
title		Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/hde1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=57829708-edc7-43d8-838f-8628d580f0d8 ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hde1.
title		Ubuntu, kernel 2.6.20-15-generic (on /dev/hde1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=57829708-edc7-43d8-838f-8628d580f0d8 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hde1.
title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/hde1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=57829708-edc7-43d8-838f-8628d580f0d8 ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hde1.
title		Ubuntu, memtest86+ (on /dev/hde1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by jimbob on 2007-06-30
In your first post you talk about hda but it appears everything you have is on hde.

Anyhow if you believe Sabayon is on hda4 (hde4) add these lines to your menu.lst and see if grub can find it:

title           Sabayon Linux on HDE4
root            (hd0,3)
kernel          /boot/kernel-genkernel-x86-2.6.20-sabayon-r3 root=/dev/hde4 
initrd          /boot/initramfs-genkernel-x86-2.6.20-sabayon-r3 
boot

________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by logos34 on 2007-06-30
> I installed Sabayon Linux first on a partition (hda4) and then Ubuntu next on to hda3. When loading grub, Ubuntu doesnt see Sabayon. I think the location of the bootloader is supposedly in 2 different locations. Sabayon said it installed it to** hda1** (which I have marked as a boot partition) and Ubuntu put it in **hda0**. Regardless of that, without (preferably) having to reinstall, how do I get my Ubuntu bootloader to recognize that Sabayon is on hda4.

You're mixing grub-speak and linux notation.  Ubuntu installed grub by default to the MBR of hde, which, since it was the first BIOS hard drive at the time, was '(hd0)'.  Sabayon looks like it put its bootloader on the other drive, hdf, which was (hd1) or the second bios boot drive.

---

