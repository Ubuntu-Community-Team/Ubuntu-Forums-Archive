---
title: "Gutsy and XP disappearance"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by wodehouse on 2008-03-30
XP boot option has disappeared from initial screen. The code for XP is still on the menu.lst. Any help for a complete beginner much appreciated.

---

### Post by Inxsible on 2008-03-30
Can you boot into XP ?

I am not sure what you mean by code for XP is still there.

---

### Post by wodehouse on 2008-03-30
Thanks for the reply.
No, I cannot boot XP anymore as the option has gone from the startup screen.
A suggested solution I found was to input sudo gedit/boot/grub/menu.lst and then add this to the bottom of the list
title Microsoft Windows XP Professional Edition
root (hd0)
savedefault
makeactive
chainloader + 1
When I opened menu.lst, this was still there untouched, so no further forward.

---

### Post by Inxsible on 2008-03-30
Can you boot into Ubuntu then?

If yes, open up a terminal and post back the output of the following command
```
sudo fdisk -l
```

---

### Post by wodehouse on 2008-03-30
Thanks again.
sudo fdisk -1 (minus one, yes?)  brings up 'invalid option- - 1'

---

### Post by Inxsible on 2008-03-30
> **wodehouse said:**
> Thanks again.
sudo fdisk -1 (minus one, yes?)  brings up 'invalid option- - 1'That's a lowercase L not 1

---

### Post by wodehouse on 2008-03-30
Hello again. Yes, I should have guessed.
There's about ten lines of stuff I would prefer not to have to copy out.
Last line says Partition table entries are not in disk order.

---

### Post by Inxsible on 2008-03-30
> **wodehouse said:**
> Hello again. Yes, I should have guessed.
There's about ten lines of stuff I would prefer not to have to copy out.
Last line says Partition table entries are not in disk order.Well its hard to help if you wont post the output. Need to see if, the XP partitions are still in there or not. You dont have to manually copy them.

You can select all those lines and then right click, and select copy and then paste it in your reply.

---

### Post by wodehouse on 2008-03-30
Thanks yet again. Now I know how to copy. Here we go.

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1899    15253686    7  HPFS/NTFS
/dev/sda2            3041        3648     4883760   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3            1900        2989     8755425   83  Linux
/dev/sda4            2990        3040      409657+   5  Extended
/dev/sda5            2990        3040      409626   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by mcduck on 2008-03-30
> **wodehouse said:**
> Thanks for the reply.
No, I cannot boot XP anymore as the option has gone from the startup screen.
A suggested solution I found was to input sudo gedit/boot/grub/menu.lst and then add this to the bottom of the list
title Microsoft Windows XP Professional Edition
root (hd0)
savedefault
makeactive
chainloader + 1
When I opened menu.lst, this was still there untouched, so no further forward.

This entry is not correct. The root line specifies only a disk, not a partition.

Replace that line with this:
root (hd0,0)

---

### Post by wodehouse on 2008-03-30
Thanks for noticing. I'm afraid it was my careless copying. But the actual menu.lst does have hd0,0, so the problem remains.

---

### Post by mcduck on 2008-03-30
In that case could you copypaste the complete menu.lst file here?

---

### Post by wodehouse on 2008-03-30
Here it is, Dr House.

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
# kopt=root=UUID=fb22b164-fe39-4988-9bcb-4892ffc87d56 ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fb22b164-fe39-4988-9bcb-4892ffc87d56 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fb22b164-fe39-4988-9bcb-4892ffc87d56 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fb22b164-fe39-4988-9bcb-4892ffc87d56 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fb22b164-fe39-4988-9bcb-4892ffc87d56 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, kernel 2.6.17-12-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-12-generic root=UUID=fb22b164-fe39-4988-9bcb-4892ffc87d56 ro quiet splash
initrd		/boot/initrd.img-2.6.17-12-generic
quiet

title		Ubuntu 7.10, kernel 2.6.17-12-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-12-generic root=UUID=fb22b164-fe39-4988-9bcb-4892ffc87d56 ro single
initrd		/boot/initrd.img-2.6.17-12-generic

title		Ubuntu 7.10, kernel 2.6.17-11-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=fb22b164-fe39-4988-9bcb-4892ffc87d56 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet

title		Ubuntu 7.10, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=fb22b164-fe39-4988-9bcb-4892ffc87d56 ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu 7.10, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=fb22b164-fe39-4988-9bcb-4892ffc87d56 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet

title		Ubuntu 7.10, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=fb22b164-fe39-4988-9bcb-4892ffc87d56 ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root




# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by mcduck on 2008-03-30
Are you sure the problem isn't just that there is not enough space in the Grub menu for all your possible boot options? You seem to have quite many entries there. Try uninstalling the old kernels with Synaptic, their Grub menu entries will be removed automatically..

(also, the second Windows entry seems quite useless as it's actually pointing to Compaq diagnostics partition.. You could remove that one manually)

---

### Post by wodehouse on 2008-03-30
Thanks very much.Sounds reasonable. Not sure what Synaptic is but I will try to find out and then follow your instructions.

---

### Post by mcduck on 2008-03-30
> **wodehouse said:**
> Thanks very much.Sounds reasonable. Not sure what Synaptic is but I will try to find out and then follow your instructions.

Synaptic package manager can be found in System/Administration/Synaptic Package Manager. It's the main tool for nstalling, removing and managing software on Ubuntu.

Just open it, search for "linux" in the package name to find all the kernel files, select all the old version packages, right-click and choose "mark for complete removal". Then click the Apply-button.

You'll find more help about using Synaptic here: [http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by wodehouse on 2008-03-30
Solution found. Too many items you said, so on startup I tried scrolling further down. Didn't think of this before because there was a large black space at the bottom of the screen. And there was the Windows XP option. I feel a fool but any beginner might fall into this trap. I will clean out the menu list as suggested.
Thanks all around. This has been a great learning experience. As you will have guessed, it's my first time to use an online forum. Bye for a goodly while, I hope.

---

