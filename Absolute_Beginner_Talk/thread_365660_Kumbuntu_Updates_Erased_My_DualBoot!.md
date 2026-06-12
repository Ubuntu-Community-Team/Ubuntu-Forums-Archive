---
title: "Kumbuntu Updates Erased My DualBoot!"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by galactus1 on 2007-02-19
I recently decided to make the transition to Ubuntu. To facilitate the switch, I decided to go with a dual boot configuration w/ windows xp and Kubuntu.  When I went over to Kubuntu to try some new stuff I noticed 80 or so updates waiting to be installed.  On the surface they looked innocent. Like a moron I just selected all of them and updated.  When I went to restart my computer the GRUB booter had 4 versions of Ubuntu and their safe modes but no option to start windows!!  What did I do!?!?  Is there any way to get back the option to start windows at the boot screen?  Why are there 4 or so versions of Ubuntu on my boot screen?  Any help would be appreciated.

---

### Post by Bachstelze on 2007-02-19
```
sudo update-grub
```

If you're lucky, it will detect your Windows and add a GRUB entry for it. If not, adding one yourself is fairly easy, post here and I - or someone else - will tell you haow to do it.

---

### Post by galactus1 on 2007-02-19
The GRUB update didn't work my fdisk is as follows:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       33638   229239517+   b  W95 FAT32
/dev/sda3   *       33639       38486    38941560   83  Linux
/dev/sda4           38487       38913     3429877+   5  Extended
/dev/sda5           38696       38913     1751053+  82  Linux swap / Solaris
/dev/sda6           38487       38695     1678729+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

my GRUB menu list is as follows:

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
# kopt=root=/dev/sda3 ro

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
# defoptions=quiet splash acpi=off

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro quiet splash acpi=off
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-27-k7
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=/dev/sda3 ro quiet splash acpi=off
initrd		/boot/initrd.img-2.6.15-27-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-k7 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-27-k7
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda3 ro quiet splash acpi=off
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda3 ro quiet splash acpi=off
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1

```
 Don't assume I know what I'm doing. I just lifted the menu and fdisk thingy from some other forum post.  They gave me the shell commands and it seemed to be required info for the other

---

### Post by Bachstelze on 2007-02-19
All right, first, I suggest you remove all the kernels you don't use - open up Synaptic and search for linux-image. Then, add those lines at the end of your menu.lst :

```

title     Windows XP
root     (hd0,0)
makeactive
chainloader +1
```

---

### Post by galactus1 on 2007-02-20
Thank You! It worked!  Now, how can I erase the other versions of Ubuntu?  I don't want to erase anything important.  Is it as easy as erasing the paragraph with the headings of the Ubuntu version I no longer want?

---

