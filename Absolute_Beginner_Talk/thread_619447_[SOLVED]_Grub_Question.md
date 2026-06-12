---
title: "[SOLVED] Grub Question"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by bbrff on 2007-11-21
My Windows partition is on /dev/sda1 ,,this is a sata drive. How would I write that in my grub file would it be (hd1,0). Im a little confused

---

### Post by overdrank on 2007-11-21
> **bbrff said:**
> My Windows partition is on /dev/sda1 ,,this is a sata drive. How would I write that in my grub file would it be (hd1,0). Im a little confused

HI this link may help
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
But remember to back up before you making changes. :)

---

### Post by MegaJim on 2007-11-21
it depends on what other drives you have installed, if you check grub's device.map it will give you a clue where grub thinks the drive is

```
cat /boot/grub/device.map
```

In general the hard drive numbers count upwards from zero starting with IDE drives in primary/secondary order then sata drives in primary/secondary order.  But this depends on your BIOS settings.

e.g. my device.map on a comp with 2 ide drives and one sata is:

```

(hd0)   /dev/hda
(hd1)   /dev/hdb
(hd2)   /dev/sda

```

partitions are generally simple and count upwards from 0 (just subtract 1)

---

### Post by kebes on 2007-11-21
> **bbrff said:**
> My Windows partition is on /dev/sda1 ,,this is a sata drive. How would I write that in my grub file would it be (hd1,0). Im a little confused

sda1 means means "first SATA disk" ("a") and first partition on that disk ("1"). Grub starts counting from zero, so "first disk, first partition" would be **hd(0,0)**. This is assuming that you only have SATA drives. (Things can get [more complicated]("http://www.mepis.org/docs/en/index.php/Grub_with_IDE_and_SATA_Drives") in mixed IDE/SATA situations.)

Hope that helps.

---

### Post by bbrff on 2007-11-21
I've tried (hd1,0) which gets me to the next screen which says starting up but then it just hangs there. This is still farther than I've gotten previously. My Sata drive is set up as a raid array. Would this make any difference or is the problem now something to do with windows

---

### Post by MegaJim on 2007-11-21
You get the windows Starting up thingamabob?

---

### Post by bbrff on 2007-11-21
No just a black screen saying Starting up and then a cursor and then.........................nothin

---

### Post by bbrff on 2007-11-21
I'm still not having much luck with my dual boot and my kids are about to mutiny. I've got a feeling like I'm sinking in quicksand and the more I try to get free the deeper I go.

---

### Post by meierfra on 2007-11-21
Try this  for windows:

title Windows
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1


It that did't work,

post the content of "menu.lst" and the output of 

```
sudo fdisk -l
```
(l is  a lower case L)

---

### Post by bbrff on 2007-11-22
When I boot to windows i get "NTLDR is missing". Here is a copy of my grub file and fdisk 


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa459a459

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   312560639   156280288+   7  HPFS/NTFS

Disk /dev/hdb: 15.3 GB, 15371919360 bytes
255 heads, 63 sectors/track, 1868 cylinders, total 30023280 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xeea4eea4

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    28659959    14329948+  83  Linux
/dev/hdb2        28659960    30009419      674730    5  Extended
/dev/hdb5        28660023    30009419      674698+  82  Linux swap / Solaris






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
default		2

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
# kopt=root=UUID=0a262a08-e693-4fc8-a765-964f7a79637f ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=0a262a08-e693-4fc8-a765-964f7a79637f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-rt
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=0a262a08-e693-4fc8-a765-964f7a79637f ro single
initrd		/boot/initrd.img-2.6.22-14-rtsudo gedit /boot/grub/menu.lstsudo gedit /boot/grub/menu.lst
sudo gedit /boot/grub/menu.lst
title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title Windows 
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

title        Microsoft Windows XP Corporate
root        (hd1,1)
savedefault
makeactive
chainloader    +1


### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by bbrff on 2007-11-22
Ive copied the ntldr and ntldr.detect files from my original windows cd onto the drive with windows on it and presto I'm back in business. Thanks to everyone for their help. Much appreciated

---

