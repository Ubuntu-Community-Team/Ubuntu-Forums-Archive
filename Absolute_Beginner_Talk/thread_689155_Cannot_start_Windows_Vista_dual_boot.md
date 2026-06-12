---
title: "Cannot start Windows Vista dual boot"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by Harryema on 2008-02-06
After deleting a partition I found that my windows vista won't boot any longer. Trying to do so from the GRUB menu results in error 22.

I tried editing the menu.lst and changing the hd0, x number to different ones and nothing would work. 

Changing it to one number would result in the boot to go to a 'windows 98' loading screen and then "Cannot find command.com please enter location" or something similar to that. 

i've also run fdisk /mbr and tried running windows vista repiar - with no avail. (actually after running the repair i was able to get the windows 98 loading screen)

It appears to be something horribly wrong with the mbr and nothing can fix that... i might try a reinstall. Perhaps one of you guys might have an idea as to what could possibly be happening. Thank you

---

### Post by ajmorris on 2008-02-06
hi there,
could you please post your grub.conf (or menu.lst) file in /boot/grub.
and also post the output of sudo fdisk -l

---

### Post by Harryema on 2008-02-06
> **ajmorris said:**
> hi there,
could you please post your grub.conf (or menu.lst) file in /boot/grub.
and also post the output of sudo fdisk -l

[QUOTE=menu.lst]# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=b3d869b4-b4c4-4aec-96be-3c80fad8bacd ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,8)

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
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b3d869b4-b4c4-4aec-96be-3c80fad8bacd ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b3d869b4-b4c4-4aec-96be-3c80fad8bacd ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,8)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1
[/QUOTE]

[QUOTE= sudo fdisk -l]
omitting empty partition (5)

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x89fcf860

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         243     1951866   1b  Hidden W95 FAT32
/dev/sda3            2156       14593    99908235    f  W95 Ext'd (LBA)
/dev/sda5            2156        7681    44387563+   7  HPFS/NTFS
/dev/sda6            7682       11119    27615703+   7  HPFS/NTFS
/dev/sda7           11120       12486    10980396   83  Linux
/dev/sda8           12487       12553      538146   82  Linux swap / Solaris
/dev/sda9           12554       14593    16386268+   7  HPFS/NTFS

[/QUOTE]


Thanks for helping.

---

### Post by ajmorris on 2008-02-07
i notice you have 3 NTFS partitions:
```
 /dev/sda5            2156        7681    44387563+   7  HPFS/NTFS
 /dev/sda6            7682       11119    27615703+   7  HPFS/NTFS
 /dev/sda9           12554       14593    16386268+   7  HPFS/NTFS
``` find which one is your vista partition, then, in your menu.lst file you have this:

```
 title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```
 
change the appropriate root (hd0,1) to your partition for vista.
GRUB does this starting from 0 however, so, if /dev/sda5 was your vista partition, root would look like this:
```
root (hd0,4)
```
then /dev/sda6:
```
root (hd0,5)
```
and /dev/sda9
```
root (hd0,8)
```

Hope that helps.

AJ

---

### Post by Harryema on 2008-02-07
Yeah, that's what I did before, and I *DID* Successfuly boot windows... well sort of. What happens is that it boots, and the loading screen shows WINDOWS 98.... which is weird cos i don't have 98 anywhere. Then it crashes and it gives me this error: "Cannot find command.com please enter location"
C:\

so... its very odd.

Any help is appreciated, thanks.

---

### Post by ajmorris on 2008-02-07
im not very proficient with windows, but it seems to me as though you have some old windows 98 files left over from some other install, and that booting vista, it cannot find the root device. However, i wouldnt think that the 98 files would be left on your vista partition, as installing windows does a format of the partition, unless you do a repair. This is why i think grub is pointing to the wrong ntfs partition

---

### Post by Harryema on 2008-02-09
I actually got the 98 boot after I did the windows mbr repair with SUPER GRUB boot. 

Could that be the problem

---

### Post by adamc83 on 2008-02-10
Hate to be the bearer of bad news, but it looks like you deleted your vista partition. See in the grub config where it says

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2

In your fdisk output there is no /dev/sda2:

Device Boot Start End Blocks Id System
/dev/sda1 * 1 243 1951866 1b Hidden W95 FAT32
/dev/sda3 2156 14593 99908235 f W95 Ext'd (LBA)
/dev/sda5 2156 7681 44387563+ 7 HPFS/NTFS
/dev/sda6 7682 11119 27615703+ 7 HPFS/NTFS
/dev/sda7 11120 12486 10980396 83 Linux
/dev/sda8 12487 12553 538146 82 Linux swap / Solaris
/dev/sda9 12554 14593 16386268+ 7 HPFS/NTFS

You'll need to recreate that partition (you can see the gap between sectors 243 and 2156 in the fdisk output there), and reinstall vista.

---

### Post by ajmorris on 2008-02-12
> **adamc83 said:**
> Hate to be the bearer of bad news, but it looks like you deleted your vista partition. See in the grub config where it says

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2

In your fdisk output there is no /dev/sda2:

Device Boot Start End Blocks Id System
/dev/sda1 * 1 243 1951866 1b Hidden W95 FAT32
/dev/sda3 2156 14593 99908235 f W95 Ext'd (LBA)
/dev/sda5 2156 7681 44387563+ 7 HPFS/NTFS
/dev/sda6 7682 11119 27615703+ 7 HPFS/NTFS
/dev/sda7 11120 12486 10980396 83 Linux
/dev/sda8 12487 12553 538146 82 Linux swap / Solaris
/dev/sda9 12554 14593 16386268+ 7 HPFS/NTFS

You'll need to recreate that partition (you can see the gap between sectors 243 and 2156 in the fdisk output there), and reinstall vista.


it could have changed from removing/deleted partitions, with the amount of NTFS partitions the OP has, i hope vista is still on there :D
and he did change grub to point to the right partition :) thats when he got the 98 boot loader problem


>  		I actually got the 98 boot after I did the windows mbr repair with SUPER GRUB boot. 

Could that be the problem


possibly, there are some other tools for doing this, i believe the vista cd can also do it :) there is a fixmbr command from the windows command prompt if you boot from the vista cd :)

---

