---
title: "Change partition flags?"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by Onay on 2007-10-28
How can I change the flags on each one of my partition?

Right now, I cannot boot into windows vista since on my hard drive my "rescue and recovery" partition is set to the /boot flag and my windows is set to the /hidden flag. How can I change this, since I cannot access windows at all!?

---

### Post by Pumalite on 2007-10-28
Use Gparted Live CD:[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
You can also install Gparted in your Ubuntu.
sudo apt-get install gparted
But I've never used it, so I'm not sure if you can change boot flags with it.

---

### Post by Onay on 2007-10-28
I did it in Gnome Partition Editor in Ubuntu, changing the flags of only those 2 ntfs partitions (windows and R&R). I reboot, attempt to get into windows, and still no changes.

Upon booting back into Ubuntu and checking the Partition editor again, the flags still remain. Should my boot flag be on the ext3 partition?

---

### Post by Pumalite on 2007-10-28
Better post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by Onay on 2007-10-28
```
matt@matt-laptop:~$ sudo fdisk -lu

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x98df319c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    10891263     5444608   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2        10901520   174394079    81746280    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *   174394080   191162159     8384040   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4       191162160   195350399     2094120   82  Linux swap / Solaris
Partition 4 does not end on cylinder boundary.
```
and...
```
matt@matt-laptop:~$ cat /boot/grub/menu.lst
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
timeout         10

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
# kopt=root=UUID=ae08a5b3-5e7c-4d88-8781-0b9b7273a018 ro

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=ae08a5b3-5e7c-4d88-8781-0b9b7273a018 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=ae08a5b3-5e7c-4d88-8781-0b9b7273a018 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


- Hide quoted text -
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Rescue and Recovery
root        (hd0,0)
parttype  (hd0,0) 0x27
unhide    (hd0,0)
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista
root        (hd0,1)
hide       (hd0,0)
chainloader    +1
```

I altered the windows and R&R entries in hopes that it would actually work, but it's still going straight to R&R every time.

I also tried changing the boot flags with the gnome partition editor. Nothing happened...

---

### Post by Onay on 2007-10-28
...?

---

### Post by Pumalite on 2007-10-28
Your recovery partition is throwing a curve here. Let's see if we can solve it this way: reinstall Grub with this: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Do 'setup (hd0,2)'

---

### Post by Onay on 2007-10-28
What about the root command? Should I root (hd0,2) as well?

---

### Post by Pumalite on 2007-10-28
Try doing just 'setup' first.

---

### Post by Onay on 2007-10-28
It didn't overwrite anything. My options are all the same, and so are the results.

According to the nasty support team over at Lenovo, they told me that my Vista partition resizing caused some kind of corruption, yet I've not seen one message telling me that it is. I just cannot get into the windows partition. I have no backups via rescue and recovery (seeing that they took up 30gb each on my 80gb hard drive...) and I cannot get into windows at all. Should I restore the MBR that came from the factory?

---

### Post by Pumalite on 2007-10-28
If you have Vista, the obvious question is: did you use the Vista partitioner to start with?. Because if not, that could be the cause of all your problems.

---

### Post by Onay on 2007-10-28
Nope, I used the partition editor in Ubuntu's Live CD...

How the heck am I supposed to fix a corrupt boot sector without a Vista CD or repair a disk without a backup? I hear that you can fix this problem using fixboot and fixmbr in the windows recovery console, but that's only for XP...

---

### Post by Pumalite on 2007-10-28
To boot either OS you can use Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
(also to repair MBR)
For partition Tables, maybe rescuecd:[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
Or TestDisk: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

