---
title: "GRUB not working properly"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by niglch on 2007-10-27
I just freshly installed Ubuntu Gusty Gibbon on my friends computer. The installation seemed to go fine and grub is installed on the MBR of his internal hard drive. He has two external hard drives and we decided to install the root partition and swap partition on the second external one listed as dev/hdc on the install CD. GRUB automatically set up Ubuntu on the menu as (hd2,2) which didn't work (error 17 I think). After doing some searching in the command prompt, we found the Linux kernel on (hd0,2). After editing the GRUB entry and booting, we got a "Starting up..." message, but after a few seconds, the computer just rebooted. Any idea how to get this working?

---

### Post by Pumalite on 2007-10-27
You have to make up your minds. You either install in an internal drive or an external one.

---

### Post by niglch on 2007-10-27
> **Pumalite said:**
> You have to make up your minds. You either install in an internal drive or an external one.
I'm not sure what you mean. I have a very similar setup at my house but of course it's a different and significantly older computer. It worked right away though, no special set up was required.
Are you saying putting GRUB on the MBR of the external hard drive will fix the issue?

---

### Post by meierfra on 2007-10-27
If the bios are able to boot from an external usb drive, your set up should work and   grub just needs some tweaking. Post the output of "cat /boot/grub/menu.lst" and "sudo fdisk -l"

And if the bios are not able to boot an usb drive, moving the MBR to the external drive won't help. In this case you will have to put  at least "/boot"  onto the internal drive.

---

### Post by niglch on 2007-11-17
I did a reinstall and made sure that GRUB was only installed on the same external hard drive as the linux root partition,
Ok, here is the output from "sudo fdisk -l"

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd579b52

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60802   488384512    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e21c271

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059349504 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xee36c443

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       22569   181285461    6  FAT16
/dev/sdc2           22570       22818     2000092+   5  Extended
/dev/sdc3           22819       30401    60910447+  83  Linux
/dev/sdc5           22570       22818     2000061   82  Linux swap / Solaris

```

And here's the menu.lst file:
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
# kopt=root=UUID=451150f0-1c7f-4402-b9d0-f4510a6e5163 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,2)

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
root		(hd2,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=451150f0-1c7f-4402-b9d0-f4510a6e5163 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd2,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=451150f0-1c7f-4402-b9d0-f4510a6e5163 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd2,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1

```

And just to be sure, here's the device.map file (it looks like it might be relevant):
```

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

```

When GRUB came up, we tried booting without changing anything and received an error 22. Then we tried changing the Ubuntu 7.10 boot entry to load from hd0,2. A "starting up..." message appeared for a few seconds and then the system restarted. I hope this is enough info,

---

### Post by meierfra on 2007-11-17
Just to make sure that I understand the situation: Is the following correct?

1) The  grub menu appears at boot up.

2)  You changed the "Grub entry"  during boot up  from "root (hd2,2) to "root (hd0,2)" 
(or did you change it in menu.lst?)


3) If your  press "c" after the grub menu appears and type "find /boot/grub/menu.lst", the output is "(hd0,2)


4)  The bios are set to boot from the harddrive containing ubuntu.

---

### Post by jaybombalous on 2007-11-17
so far u have mentioned two errors 17 and 22. So which is it and when did u get both of them.

The point is, when u get an error u look it up to see what the error means. Then u can go about diagnosing the problem. 

So lets have it, which error was it again?

---

### Post by jaybombalous on 2007-11-17
There is no doubt about it, linux is located at hd (2,2) from the info u provided. so where did u write grub too? Which device?

---

### Post by niglch on 2007-11-17
Meierfra,
1) Yes, the boot menu does appear at startup
2) The GRUB entry was changed at the boot menu, menu.lst was left unmodified.
3) Yes, pressing "c" and typing "find /boot/grub/menu.lst" produces the output "(hd0,2)
4) Yes, the bios is set to boot from the drive containing Ubuntu (the external one).

jaybombalous,
Error 22 (no partition) appeared when trying to boot Ubuntu with the first command left as "root (hd2,2)". When I initially mentioned error 17, I was wrong. It was error 22. After editing the command to be "root (hd0,2)", I got the "Starting up" message, but the computer spontaniously restarted after about 15 seconds. What is strange here is that I know I installed Ubuntu on /dev/hdc. According to the device.map file, this should be what GRUB sees as (hd2,2). However, when booting, entering the GRUB console and typing "find /boot/grub/menu.lst", produces the output (hd0,2), which seems to be the wrong hard drive. According to all of the other files, this should have come up as (hd2,2). I'm not sure what exactly is going on.
Also, I know that GRUB is installed on the boot sector of the same external drive Ubuntu is on because when I turn of that drive, Vista will boot automatically at startup.

---

### Post by meierfra on 2007-11-17
> According to the device.map file, this should be what GRUB sees as (hd2,2). However, when booting, entering the GRUB console and typing "find /boot/grub/menu.lst", produces the output (hd0,2), 


At boot up, grub numbers the hard drives in the boot order (starting at 0). So the hard drive the computers boots from is always (hd0).  If ubuntu would be smart enough it would have used (hd0,2) in menu.lst, but it seems to always get that wrong. 


But I do not understand why you cannot boot after you changed (hd2,2) to (hd0,2). 


Try this: Press c at the grub-menu to get to the command line. Type

root (hd0,2)

setup (hd0)

halt


Then hope for the best and reboot

---

### Post by niglch on 2007-11-17
Agh, still no luck. It's really a shame because the computer is brand new, custom built, and quite nice. I was wondering how fast and nice Ubuntu would look on it. It just seems like there's a problem getting past that "Starting Up..." message. There's no error that comes up though, the system just reboots. Maybe there was a problem with the install CD... I might try making another and installing again to see if that works.

---

### Post by meierfra on 2007-11-17
> Agh, still no luck.

That's actually what I expected.  Before reinstalling you might give Supergrub a chance.
Information on Supergrub: [ Hermanzone]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by meierfra on 2007-11-17
Since I'm not convinced that reinstalling will solve your problem, here is another thing to try:

Unplug the other two hard drives. (You still would have to change (hd2,2) to (hd0,2) , either at the boot menu or in menu.lst)

---

