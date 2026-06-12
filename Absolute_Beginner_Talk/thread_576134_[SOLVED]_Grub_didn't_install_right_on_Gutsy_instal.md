---
title: "[SOLVED] Grub didn't install right on Gutsy install."
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by nowhere@cox.net on 2007-10-14
HELP!

On hour 3 now in the forums and grub docs trying to figure out how to change all the hd0's and hd1's for my pathetically simply install to bring up grub and allow me to boot anything.

I have two drives, IDE 80GB, and SATA 120GB. Ubuntu is supposed to be on IDE and windows on SATA.

Right now I am getting a Error 17 when booting. So I can't get to windows or Ubuntu. Here is fdisk:
```
ubuntu@ubuntu:/$ sudo fdisk -l

Disk /dev/hdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x065a0659

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        9352    75119908+  83  Linux
/dev/hdd2            9353        9729     3028252+   5  Extended
/dev/hdd5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20502050

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14592   117210208+   7  HPFS/NTFS

```

Here is device.map
```
ubuntu@ubuntu:/mnt/boot/grub$ more device.map
(hd0)   /dev/hdd
(hd1)   /dev/sda

```

here is menu.lst
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
# kopt=root=UUID=2ca1faad-f496-49b0-9e87-55d35714cbce ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2ca1faad-f496-49b0-9e87-55d35714cbce ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2ca1faad-f496-49b0-9e87-55d35714cbce ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
#map		(hd0) (hd1)
#map		(hd1) (hd0)
chainloader	+1

```

In case you need it 
```
grub> find /boot/grub/stage1
 (hd0,0)

```



I sure would love some help!

Thanks a ton,
Eric

---

### Post by louieb on 2007-10-14
Rather that reinvent the wheel look here [Gentoo Linux Grub Error Collection]("http://www.gentoo.org/doc/en/grub-error-guide.xml")

---

### Post by vgrisham on 2007-10-14
[This]("http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch08.html") tutorial explains how one can use a live cd to restore grub.

---

### Post by nowhere@cox.net on 2007-10-14
Hey! Thanks for replying so quick. Unfortunately those links were not any help. The Gentoo had only this for my error:
 ```
5. Grub Error 17

Situation

Code Listing 5.1: Grub Output

root (hd0,0)
filesystem type unknown partition type 0x7

Error 17 : Cannot mount selected partition

Solution

This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

Be sure to check your root(x,y) settings in your grub.conf.

Also, if you are trying to boot Windows, make sure that your grub.conf file has the root (hdX,Y) (or rootnoverify (hdX,Y)) and chainloader (hdX,Y)+1 in it. 
```

I'm sorry but "check your root(x,y) settings in grub.conf" means very little to me. I didn't even think there was a grub.conf...

The other link said:
```
8.6. 	

How to restore GRUB menu after Windows installation?
	

   1.

      Read How to use a Ubuntu installation CD to gain root user access?
   2.

      Assuming that /dev/hda is the location of /boot partition
   3.

      # grub-install /dev/hda
```

which wasn't the problem either. I'm pretty sure grub is installed but didn't like wherever the config files were telling it to boot.

I'm going to try the liveCD install with a fresh install since I figured out it doesnt crash totally if I select safe graphics mode.

I'll post again if I still cant get grub to work...

Thanks again!

Eric

---

### Post by alienexplorers on 2007-10-14
Which operating system is supposed to be your primary (Windows or Ubuntu).

---

### Post by nowhere@cox.net on 2007-10-14
Doesn't really matter. I had Feisty running and moved the windows stuff to the top of the menu.lst file so it booted by default if my wife needed to print on my shared printer. 

The boot order in the bios has the SATA drive (sda) booting first. 

The fresh install didn't work btw. Same error. Error 17, no other information.

I appreciate the help trying to sort this out...

Eric

---

### Post by nowhere@cox.net on 2007-10-14
BTW When I tried grub-install /dev/hdd  I get:

```
ubuntu@ubuntu:~$ sudo grub-install /dev/hdd
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

```

Again, I don't really know how to interpret this either...

Eric

---

### Post by nowhere@cox.net on 2007-10-14
My Feisty setup which DID work was the following...

device.map
```
(hd0)	/dev/hdd
(hd1)	/dev/sda
```

menu.lst
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
# kopt=root=UUID=87579504-f3bf-4627-85a4-fc9c8521f9cc ro

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
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
#map		(hd0) (hd1)
#map		(hd1) (hd0)
chainloader	+1

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=87579504-f3bf-4627-85a4-fc9c8521f9cc ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=87579504-f3bf-4627-85a4-fc9c8521f9cc ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=87579504-f3bf-4627-85a4-fc9c8521f9cc ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=87579504-f3bf-4627-85a4-fc9c8521f9cc ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root



```

BUT Feisty was installed on the second partition. 

Thanks,
Eric

---

### Post by louieb on 2007-10-15
Wild as guess for today.
```

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=2ca1faad-f496-49b0-9e87-55d35714cbce ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic

title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

```grub.conf aka menu.lst :   just depends on the distro, most use the later.

All Gentoo is saying is check the partition your **root **statement points to.
Looking at your fdisk output there are only 2 choices (hd0,0) or (hd1,0) my best guess is (hd0,0).

---

### Post by anaconda on 2007-10-15
louieb
is propably right.
sometimes there is problems if you have both IDE and SATA drive, and ubuntu will incorrectly guess the booting order of the drives. (happened to me too.)

changing the hd1 to hd0 and vice versa should help.

---

### Post by nowhere@cox.net on 2007-10-15
Hey all.  Thanks a ton for trying to help out! I finally got it working last night bout 2am. YAWN!  What I had to do was boot from the LiveCD in safe graphics mode. The I launched ubiquity in a terminal with the no-migration-assistant flag.

After the install finished I was finally able to see the grub menu which i wasn't even getting before but the boot order was still messed up. It was a simple thing to reverse all the hd0's and hd1 in the menu.lst file and I had to remove the mapping statement from the windows entry.  I finally got it booted and ran the updates and had forgotten to change the #groot statement so the update changed it all back. 

Anyway, good news is that it is all working, and once in the default driver it chose for my nvidia card worked well enough to get my restricted drivers installed.  I had fully expected x to crash since the LiveCD would not start x with it's default driver.

Total install time: 19 hours over three days.

Compiz is kinda cool tho...

Thanks for the help!
Eric

---

