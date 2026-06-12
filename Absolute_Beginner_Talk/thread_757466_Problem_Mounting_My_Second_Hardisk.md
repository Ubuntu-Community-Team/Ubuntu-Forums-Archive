---
title: "Problem Mounting My Second Hardisk"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by itsvan on 2008-04-16
Hello everyone, im trying to make UBUNTU have both of my hardrive work with eachother,,so i can swap files from one to another,,but it wont mount my second hardisk,,,my second hardisk has WINDOWS XP on it,,but when i first got ubuntu installed i was able to,,now i cant,,please i need some help!!!:confused:

---

### Post by talsemgeest on 2008-04-17
Type the following in the terminal and post the output: ```
cat /etc/fstab
```

---

### Post by itsvan on 2008-04-17
ok here it is!

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=5a1ad86c-8c5a-44bd-8ccb-b2ad7c5218a7 /               reiserfs defaults        0       1
# /dev/hda1
UUID=70690846-be73-410c-af5c-91b19908667c /boot           reiserfs notail          0       2
# /dev/hda4
UUID=af2466c3-1982-4b33-bfa7-c17fb38e6cb1 /home           reiserfs defaults        0       2
# /dev/sda1
/dev/sda1 /media/disk ntfs-3g defaults, force 0 0
# /dev/hda2
UUID=f942297f-6c80-4d85-ad1e-f4039704c53a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by itsvan on 2008-04-19
Please Help!!!!!!!!

---

### Post by |{urse on 2008-04-19
wait a minute.. your windows patition is already mounted

---

### Post by |{urse on 2008-04-19
> **itsvan said:**
> ok here it is!

# /etc/fstab: static file system information.
# /dev/sda1
/dev/sda1 /media/disk ntfs-3g defaults, force 0 0


just cd /media/disk

viola

or if you want to see it in a window

nautilus /media/disk

---

### Post by itsvan on 2008-04-20
so what do i do? usually there used to be an icon that let me go into my other hardrive, and i could transfer stuff or whatever,,now i do not see it,

---

### Post by talsemgeest on 2008-04-20
Because it is now mounted as a directory. Your hard drive is now at  /media/disk.

---

### Post by alpdo on 2008-04-20
sudo mount -a

---

### Post by itsvan on 2008-04-21
[mntent]: line 12 in /etc/fstab is bad



thats what i got when i tried sudo mount-a

---

### Post by talsemgeest on 2008-04-21
It looks fine to me. Try removing the line and rebooting, then mounting the harddrive manually.

---

### Post by alpdo on 2008-04-21
/media/disk ntfs-3g defaults, force 0 0

try this at line 12...

---

### Post by vanadium on 2008-04-21
There is an extraneous space before "force"which causes the error. However, I strongly recommend you to remove the force option altogether if you care about the data on that drive.

1) Change line 12 to:

/dev/sda1 /media/disk ntfs-3g defaults 0 0

2) Shut down Ubuntu, start Windows XP, shedule a disk check at next reboot. Shut down and restart Windows to have the disk check. Then shut down Windows completely (no hibernate).

3) Start Ubuntu again: the second harddisk should be mounted and be accessible under /media/disk

With a dual boot system, you have to take care to always exit Windows completely before booting Ubuntu. This is because the drive should be properly closed before Ubuntu will mount it (without forcing it).

Using the "force" option will make it mount always, but if the disk is not clean, mounting and using it anyway could lead to further damage of the volume. "force" is good for recovering data in an emergency situation, but should not be used daily.

---

### Post by itsvan on 2008-04-22
Hey guys you know its weird,,every command i put it it keeps on telling me either some error,,or that it doesn't exist or anything around those lines,,do you think it could be a problem with that partition,,because at the boot screen i do not see Windows Xp any more,,even though this was a problem before that, now i do not see that option,,and that happened when i installed ubuntu studio,,which now it gives me two options of them,,,but whats weird no matter which one i choose it takes me to what it seems the same place...
again im fairly new at ubuntu,,so im trying me best to get this fixed,,its ridiculous,,what are the wise words?

---

### Post by talsemgeest on 2008-04-23
Ok just to get a bit more information, type this and post the output: ```
sudo fdisk -l
```

---

### Post by itsvan on 2008-04-23
hey hers the output to sudo fdisk -l




Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41934192

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6fef6fef

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         124      995998+  83  Linux
/dev/hda2   *         125         610     3903795   82  Linux swap / Solaris
/dev/hda3             611        4865    34178287+  83  Linux
/dev/hda4            4866       10011    41335245   83  Linux

---

### Post by itsvan on 2008-04-24
any suggestions?,,

---

### Post by bumanie on 2008-04-24
Post ouput of > cat /boot/grub/menu.lst
Also am bemused by the fact that the boot flag for linux is in your swap partition at hda2.

---

### Post by itsvan on 2008-04-24
here's the output...



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
# kopt=root=UUID=5a1ad86c-8c5a-44bd-8ccb-b2ad7c5218a7 ro

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

title           Ubuntu 7.10, kernel 2.6.22-14-rt
root            (hd0,0)
kernel          /vmlinuz-2.6.22-14-rt root=UUID=5a1ad86c-8c5a-44bd-8ccb-b2ad7c5218a7 ro quiet splash
initrd          /initrd.img-2.6.22-14-rt
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.22-14-rt root=UUID=5a1ad86c-8c5a-44bd-8ccb-b2ad7c5218a7 ro single
initrd          /initrd.img-2.6.22-14-rt

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.22-14-generic root=UUID=5a1ad86c-8c5a-44bd-8ccb-b2ad7c5218a7 ro quiet splash
initrd          /initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.22-14-generic root=UUID=5a1ad86c-8c5a-44bd-8ccb-b2ad7c5218a7 ro single
initrd          /initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /memtest86+.bin
quiet

---

### Post by itsvan on 2008-04-27
by the way i installed ubuntu hardy heron,,and now i see an available 80 gig hardrive,,wich i belive is windows xp,,but i still cant transfer anything to it,,what can i do?

---

### Post by talsemgeest on 2008-04-27
Try fire up gparted, right click the partition and click information. See what that tells you.

---

