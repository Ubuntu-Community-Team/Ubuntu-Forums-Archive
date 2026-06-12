---
title: "Stuck on live cd after update"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by randiroo76073 on 2006-12-07
After updating kernel thru Ubuntu updater menu.lst zonked, how do I edit from live cd, it's on hda16 & I have to go thru terminal-"gksu disks-admin" to enable, but then can't edit menu.lst from there. Please remember "kiss"
TIAFAI :confused:

Oops, forgot, I'm running Dapper 6.06LTS

---

### Post by randiroo76073 on 2006-12-07
Will this work: ubuntu@ubuntu:~$ chown ubuntu /dev/hda16/boot/grub/menu.lst
If yes, I'll chown back to root when up & running in installed

---

### Post by randiroo76073 on 2006-12-07
Alright what good is the edit in grub startup menu, it doesen't seem to do anything except pyo, I edited grub 4 times and none of them stuck, is there a secret to it, someone please tell me! Still no luck on getting to menu.lst.
This is what it should be:

# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
#timeout=15

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
# kopt=root=/dev/hda11 ro ramdisk_size=100000 lang=us apm=power-off nomce vga=791

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,10)

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
# defoptions=

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery mode) single
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

# Pretty colours
color cyan/blue white/blue

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
#timeout=15

## ## End Default Options ##
### BEGIN AUTOMAGIC KERNELS LIST

title Ubuntu at hda16, kernel 2.6.15-23-386
root (hd0,15)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda16 ro quiet splash
initrd /boot/initrd.img-2.6.15-23-386
savedefault
boot

title Ubuntu recovery mode
root (hd0,15)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda16 ro single
initrd /boot/initrd.img-2.6.15-23-386
boot

title memtest86+
root (hd0,15)
kernel /boot/memtest86+.bin
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda5.
title PC linuxos at hda5
root (hd0,4)
kernel /boot/vmlinuz-2.6.12-oci6.mdk-i586-up-1GB root=/dev/hda5 ro noapic nolapic acpi=ht nomce psmouse.proto=imps splash=silent
initrd /boot/initrd-2.6.12-oci6.mdk-i586-up-1GB.img
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda7.
title MEPIS at hda7, kernel 2.6.15-26-386
root (hd0,6)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda7 nomce quiet vga=791
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda9.
title Kubuntu at hda9, kernel 2.6.15-23-386
root (hd0,
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda9 ro quiet splash
initrd /boot/initrd.img-2.6.15-23-386
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda10.
title Kanotix at hda11, kernel 2.6.16.16-kanotix-1
root (hd0,10)
kernel /boot/vmlinuz-2.6.16.16-kanotix-1 root=/dev/hda11 ro ramdisk_size=100000 lang=us apm=power-off nomce vga=791
initrd /boot/initrd.img-2.6.16.16-kanotix-1
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda15.
title Freespire at hda15, Ver. 1.0.2
root (hd0,14)
kernel /boot/vmlinuz-2.6.14-gratis root=/dev/ide/host0/bus0/target0/lun0/part15 rootdev=0x030f ramdisk=35392 video=vesafb:nomtrr jiffymount=noatime mem=nopentium resume2= vga=0x311 splash=silent
initrd /boot/initrd-2.6.14-gratis.gz
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
title Windoz 98me on hda1
root (hd0,0)
makeactive
chainloader +1

Smilie face= (_8_)

---

### Post by randiroo76073 on 2006-12-08
This thread should solve alot of Grub boot problems:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

