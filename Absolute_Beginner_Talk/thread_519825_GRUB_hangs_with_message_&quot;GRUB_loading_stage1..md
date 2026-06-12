---
title: "GRUB hangs with message &quot;GRUB loading stage1.5.&quot;"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by doragasu on 2007-08-07
I have installed Ubuntu 7.04, 64 bit, desktop and I can't get it to boot. Every time I try to boot it, GRUB  hangs with message: "GRUB loading stage 1.5.".

My PC is an AMD64 3200+, 1GB RAM, RADEON 9600 Pro and 200 GiB SATA HDD.

I know the HDD is working because booting with the live CD I can mount the Ubuntu partition and see the installed files. Also I had previously Win XP running on my machine.

I have tried without success manually copying the sda devices to the target /dev folder (because it looked like the installer didn't create them).

I have also created a boot floppy using 'grub-floppy', but this doesn't work, when I try to boot from the floppy, GRUB hangs with message "GRUB loading stage 2.".

Any ideas about getting this to work would be greatly appreciated.

Thanks in advance.

---

### Post by Pragmatist on 2007-08-07
> **doragasu said:**
> ....GRUB  hangs with message: "GRUB loading stage 1.5."....I have also created a boot floppy using 'grub-floppy', but this doesn't work, when I try to boot from the floppy, GRUB hangs with message "GRUB loading stage 2."....
To quote from: "Linux+ 2005 In Depth, by Eckert and Schitka",
"Stage 1.5 loads filesystem support and proceeds to Stage 2.  Stage 2 performs the actual boot loader functions and displays a graphical boot loader screen..."

So before using the boot floppy, there was some issue with your filesystem.  After using the floppy, there is some other issue.  In both cases, we need to see **/boot/grub/menu.lst**

> **doragasu said:**
> I have tried without success manually copying the sda devices to the target /dev folder (because it looked like the installer didn't create them).
Since Udev, device files are created dynamically.  If they aren't needed, they aren't created.  Why do you think you need /dev/sda?

---

### Post by psusi on 2007-08-07
Yes, do not mess with /dev.  Attempting to copy sda will copy the entire contents of the hard drive, not the sda dev node.

---

### Post by doragasu on 2007-08-07
Thanks a lot for your help.

I think sda is needed (along with sdN with N being partition number) because I'm using a SATA disk. To copy the devices I mounted target partition in /target and used the the following command (as root):

```
cp -a /dev/sd* /target/dev/
```

I think devices should be OK, but if they're not needed, I'll reinstall the system and I'll not copy them.

Contents of my automatically generated menu.lst are:
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
# kopt=root=UUID=29e0da6b-369a-4d71-a9b8-d8050d716694 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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
# defoptions=quiet splash locale=es_ES

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
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=29e0da6b-369a-4d71-a9b8-d8050d716694 ro quiet splash locale=es_ES
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=29e0da6b-369a-4d71-a9b8-d8050d716694 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

As you should guess seing the file, Ubuntu is installed in partition /dev/sda7

I'm suspecting that the menu.lst file doesn't even get readed, because I don't see any error messages, the system hangs without showing anything. Maybe GRUB is doing something that my disk controller doesn't like or something like this.

---

### Post by Pragmatist on 2007-08-07
I've never seen this character: $ 
in a menu.lst file

BEFORE MAKING ANY OF THE SUGGESTED CHANGES, BACKUP THE FILE!

One change I would try is just to remove the "$"

root=UUID=013cb0de-8ab6-4419-9b$

becomes

root=UUID=013cb0de-8ab6-4419-9b

Another change I would try, is to create entries that do not use UUID.  I would do this at least for testing purposes.  Here is an example:

```
 title           Ubuntu, kernel 2.6.20-15-generic (on /dev/sda7)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.20-15-generic root=/dev/sda7 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sda7)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.20-15-generic root=/dev/sda7 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
```

---

### Post by doragasu on 2007-08-07
I'm sorry, I didn't copy/paste properly the menu.lst file. I have edited my previous post with the correct version of the menu.lst file. Also I'm going to try removing the UUID string as you suggested to see what happens.

---

### Post by cobrn1 on 2007-08-07
Maybe a stupid idea, but have you tried using the Super GRUB disc to fix this?

I'm not sure if it's applicable to your situation, but I had a similar error (after reinstalling windows and messing about) and used the disc to write GRUB back to the MBR...

Look it up on google, it may be of some help (if not today, maybe another time - it's saved my hide afew times now... ;) )

---

### Post by doragasu on 2007-08-08
I have tried installed the i386 version of Ubuntu 7.04 without luck. Then I have tried installing SuSE 9.2 and it also hangs, now with message "GRUB loading stage 2..". The interesting thing about the SuSE distro is that I can boot the system booting from the CD, selecting "Installation" and then "Boot installed system". If instead of selecting "Installation" in the CD menu I select "Boot from hard disk", it also hangs with the "GRUB loading stage 2.." message.

I don't know what to do, the disk works because I could boot Win XP without problems...

---

### Post by psusi on 2007-08-08
The /dev on the hard disk when you mount it from the livecd should be empty.  /dev does not actually exist on disk; it is mounted as a ramdisk and its contents are created dynamically as the actual hardware it represents is detected.

As for the grub problem, please post the output of fdisk -l

---

### Post by doragasu on 2007-08-08
I have deleted and re-created the partitions and re-installed the system. Now it's in /dev/sda3. fdisk -l reports (note it's in spanish, if you need it I can translate it but I suppose it's not needed):

```
root@ubuntu:~# fdisk -l

Disco /dev/sda: 200.0 GB, 200049647616 bytes
255 cabezas, 63 sectores/pista, 24321 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       17946   144151213+   7  HPFS/NTFS
/dev/sda2           24079       24321     1951897+  82  Linux swap / Solaris
/dev/sda3           17947       24078    49255290   83  Linux

Las entradas de la tabla de particiones no están en el orden del disco
```

The contents of the menu.lst file are:

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
# kopt=root=UUID=89489892-2c31-4fc5-b01d-872906357937 ro

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
# defoptions=quiet splash locale=es_ES

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
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=89489892-2c31-4fc5-b01d-872906357937 ro quiet splash locale=es_ES
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=89489892-2c31-4fc5-b01d-872906357937 ro single
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

I have also tried GAG bootloader and guess what... it doesn't work for me. When I select Linux to boot, a "Invalid boot sector" message pops up...

---

### Post by Pragmatist on 2007-08-08
> **doragasu said:**
> I have also tried GAG bootloader and guess what... it doesn't work for me. When I select Linux to boot, a **"Invalid boot sector"** message pops up...
Are you using a SATA drive?  Do you have any other hard drives on your computer?  Did you install grub to the MBR?  What other OS are on the hard drive?

This is an excellent how to for grub (read the section about SATA):
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by psusi on 2007-08-08
Your bios may not be able to see beyond 8 gb on the disk.  Try using the super grub disk to boot and when you get to the grub prompt, try issuing a find /stage2 command.

---

### Post by doragasu on 2007-08-08
To pragmatist:
- I'm using a SATA disk (it's the only HDD plugged to my PC).
- GRUB is installed in the MBR.
- I have also Windows XP installed. I'm able to boot Windows XP using [GAG Boot Manager](http://gag.sourceforge.net/) installed to a floppy, but using this manager I'm not able to boot Ubuntu.
- I'm having a loog to the Grub Howto right now, thanks.

To psusi: I also tried to install Ubuntu alone in the hard disk, using a ext3 partition from the start of the disk to the end minus 2 GB used by the swap partition. It also didn't work. I've also tried Super Grub burned to a CD and it also freezes at "Loading Stage 2.".

---

### Post by psusi on 2007-08-09
Try installing ubuntu with a 100 MB /boot partition at the start of the disk.

---

### Post by doragasu on 2007-08-09
Finally I got it to work. I have installed LILO in the Ubuntu partition (not in the MBR) and GAG in the MBR. Using GAG I can boot Win XP or Ubuntu (loaded using LILO).

Thanks for the tips.

---

