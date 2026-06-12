---
title: "GRUB won't boot Ubuntu"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by SlaughterDog on 2007-05-25
After using [this tutorial](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub) on how to set GRUB back on the MBR, GRUB appears but won't boot Ubuntu. My option for Ubuntu is Linux kernel 2.6.20-15-generic (I say this because I have Ubuntu 7.04 and I don't know what version the kernel should be), and it says "Error 15: Couldn't find file" when I try to select it. How do I fix this?

---

### Post by darkworld on 2007-05-25
Can you go into your ubuntu using livecd then get your grub menu list.

> gedit /boot/grub/menu.lst

Post info please.

---

### Post by darkworld on 2007-05-25
just for good measure can you post the results of these too.


> ls -l /boot

and

> ls -l /boot/grub

and become root and

> fdisk -l

---

### Post by SlaughterDog on 2007-05-25
So menu.lst is blank.

Other commands:
```

ubuntu@ubuntu:~$ ls -l /boot
total 9755
-rw-r--r-- 1 root root  414210 2007-04-15 08:07 abi-2.6.20-15-generic
-rw-r--r-- 1 root root   83234 2007-04-15 05:33 config-2.6.20-15-generic
-rw-r--r-- 1 root root 6842512 2007-04-15 11:56 initrd.img-2.6.20-15-generic.bak
-rw-r--r-- 1 root root   94600 2006-10-20 11:44 memtest86+.bin
-rw-r--r-- 1 root root  806942 2007-04-15 08:08 System.map-2.6.20-15-generic
-rw-r--r-- 1 root root 1745100 2007-04-15 08:07 vmlinuz-2.6.20-15-generic

ubuntu@ubuntu:~$ ls -l /boot/grub
ls: /boot/grub: No such file or directory

ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14023   112639716    7  HPFS/NTFS
/dev/sda2           14024       16708    21567262+   c  W95 FAT32 (LBA)
/dev/sda3           16709       19337    21117442+  83  Linux
/dev/sda4           19338       19457      963900    5  Extended
/dev/sda5           19338       19457      963868+  82  Linux swap / Solaris

```

---

### Post by SlaughterDog on 2007-05-25
And the contents of menu.lst
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
# kopt=root=UUID=71065279-1aea-435c-af2a-74e377f4b8fb ro

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=71065279-1aea-435c-af2a-74e377f4b8fb ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=71065279-1aea-435c-af2a-74e377f4b8fb ro single
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
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by darkworld on 2007-05-25
grub directory is missing but maybe the livecd running is confusing things...? Because you can gui to /boot/grub/menu.lst but ls -l /boot/grub doesnt output.

After you reinstalled grub did you 

> sudo update-grub

do that if you didnt.


The directing to your kernel must be wrong. Because it cant find it.... thinking....thats the problem

---

### Post by SlaughterDog on 2007-05-25
Then it says there's no grub directory.

---

### Post by SlaughterDog on 2007-05-30
Well, I guess ima reinstall Ubuntu. How shall I do that, delete the existing ext3 partition first?

---

### Post by confused57 on 2007-05-30
> **SlaughterDog said:**
> Well, I guess ima reinstall Ubuntu. How shall I do that, delete the existing ext3 partition first?
Have you tried root (hd0,2) to boot Ubuntu?  If you get a grub boot menu, hightlight your Ubuntu entry, press "e", then change root to (hd0,2), then press "b" to boot.

Yes, you can just reinstall over top of your existing ext3 partitions, just select to format.

You have to mount your Ubuntu root partition from the live cd to explore your installed Ubuntu:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

---

### Post by SlaughterDog on 2007-06-01
I tried that, no dice. I reinstalled and everything's honky-dory again.

---

### Post by rillip on 2007-06-01
Well, it's a moot point now, but I think I see what the problem was.

Here's your menu.lst

initrd		/boot/initrd.img-2.6.20-15-generic


Here's your file structure:
-rw-r--r-- 1 root root 6842512 2007-04-15 11:56 initrd.img-2.6.20-15-generic.bak

It's looking for the image, but it's named image.bak

I think that's what was causing the 404.  You probably could have just mounted the drive and installed a new kernel.  Ah well, what's done is done, at least it's working now. :)

---

