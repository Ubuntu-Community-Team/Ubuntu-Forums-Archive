---
title: "[SOLVED] Help! Vista won't Boot!"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by mthakur2006 on 2007-12-28
Hi,
I just installed Ubuntu on my brother's laptop which had Vista on it before. Now, when it gets to grub, Ubuntu boots fine but when I select Windows, the laptop just reboots.
Please help, it's urgent.
Thanks.

---

### Post by jas0 on 2007-12-28
Please provide us with the following information:

```
cat /boot/grub/menu.lst
cat /boot/grub/device.map
sudo fdisk -l
```

---

### Post by mthakur2006 on 2007-12-28
> **jas0 said:**
> Please provide us with the following information:

```
cat /boot/grub/menu.lst
cat /boot/grub/device.map
sudo fdisk -l
```

cat /boot/grub/menu.lst:

```
 mtha@ubuntu:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=947ce111-af9b-463e-afd5-4c9f3d4d2adb ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=947ce111-af9b-463e-afd5-4c9f3d4d2adb ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=947ce111-af9b-463e-afd5-4c9f3d4d2adb ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,3)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista/Longhorn (loader)
root            (hd0,1)
savedefault
makeactive
chainloader     +1

```

cat /boot/grub/device.map

```
 cat /boot/grub/device.map 
(hd0)   /dev/sda

```

and, sudo fdisk -l
```
 mtha@ubuntu:~$ sudo fdisk -l
[sudo] password for mtha:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c043d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        4982    38476562+   7  HPFS/NTFS
/dev/sda3            4982        5020      309563+  82  Linux swap / Solaris
/dev/sda4            5021        7296    18281970   83  Linux
mtha@ubuntu:~$ 

```
Thanks.

---

### Post by LaRoza on 2007-12-28
Try:

```

gksudo gedit /boot/grub/menu.lst

```

Add:

```

itle           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

To the end of the above file, and reboot.

Choose that entry (if it is at the end, it will be the last one)

---

### Post by mthakur2006 on 2007-12-28
Hi,
It doesn't work, says BOOTMGR NOT FOUND, Press CTRL+ALT+DELETE to restart   :(

---

### Post by LaRoza on 2007-12-28
> **mthakur2006 said:**
> Hi,
It doesn't work, says BOOTMGR NOT FOUND, Press CTRL+ALT+DELETE to restart   :(

Rats.

Well, you will still be able to get your data from the Ubuntu install.

It looks like (to me, with my little experience) that Ubuntu is corrupted. 

What did you use to alter the partitions? If GParted, what version?

---

### Post by mthakur2006 on 2007-12-28
i had tried to install opensuse just before that and that is what caused this mess :(
does it mean i will have to reinstall vista? even more :( :(

---

### Post by Goop on 2007-12-28
I'm not an expert, but the "BOOTMGR" error sounds like Vista's bootloader failing. Your other installs shouldn't be affected unless something went terribly wrong. Do you have a Vista CD you can boot from? If so there should be an option, somewhere (I haven't used it myself) to boot into a recovery console. I think the command to run (in Vista's recovery console) is:

```
bootrec /fixmbr
```

-or it could be either of those words in there, try both. You could also try using the Ubuntu terminal or a Super GRUB Disk to make GRUB regenerate it's bootloader. From the Ubuntu terminal, the command is:

```
sudo grub
```

At the "grub>" prompt, type:

```
root (hd0,7)
setup (hd0)
quit
```

And be sure to replace (hd0,**7**) with the right hard drive and partition.

Hope this helps.

---

### Post by dstew on 2007-12-28
I think the Vista recovery command you need to use is FixBoot rather than FixMbr. The FixMbr will remove the grub boot loader from the disk's Master Boot Record. I think you only need to fix the Vista boot sector of the sda2 partition with FixBoot.
See [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by meindian523 on 2007-12-28
Um,if we see the fdisk -l,we have the boot flag on /dev/sda2 and the menu.lst points to (hd0,1)

Are we sure that the C:\ of Vista is the second partition and not the first partition on the HDD?

---

### Post by billgoldberg on 2007-12-28
If its just a booting problem, download "super grub disk". Burn the iso to cd.

And use that to boot into vista/repair the grub/vista mbr, ...

---

### Post by mthakur2006 on 2007-12-28
still no luck guys :(

---

### Post by mthakur2006 on 2007-12-28
Guys I managed to fix it............finally!
What I did was boot into the GRUB super disk and 'activate the windows partition' and fix the boot as well. Then I booted into the rescue CD of vista and it offered to repair everything by itself so i took the option and voila......i was booting into vista!!
i can reload the grub to boot into ubuntu another time ;)
thanks guys for your support once again.

---

### Post by meindian523 on 2007-12-28
Can you boot into Ubuntu as well as Vista?

---

### Post by jas0 on 2007-12-28
> **mthakur2006 said:**
> Guys I managed to fix it............finally!
What I did was boot into the GRUB super disk and 'activate the windows partition' and fix the boot as well. Then I booted into the rescue CD of vista and it offered to repair everything by itself so i took the option and voila......i was booting into vista!!
i can reload the grub to boot into ubuntu another time ;)
thanks guys for your support once again.

Please do me a favor and post the files I asked about in the beginning of this thread when you get your Ubuntu running. I would love to see if there is any difference and what it is. 

Thanks!

---

