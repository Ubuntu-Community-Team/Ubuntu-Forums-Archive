---
title: "root file system...."
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by theophane.weber on 2007-02-12
Hello,

I am trying something a bit different than my previous installation of ubuntu; mainly, I have a XP/Ubuntu installation and used to install XP first, then Ubuntu and let GRUB take care of the boot. I am trying to do it the opposite way, by installing ubuntu first, saving the boot information, and modifying my boot options in XP.
It works fine, except that while my computer used to hang up sometimes at "mounting root file system", it now does all the time. I know this question has been asked countless and countless times, but for that very reason it is impossible to look up an answer to that problem in google, given that so many people have posted their version of the problem, these posts come up first in google (as a matter of fact, besides disabling USB2, which I am not too excited to do, i haven't seen any solution). So... I was wondering: what's the problem with all these root filesystems? How can I diagnose what's going wrong with my computer in particular..? (and how can I fix it? :) )

thanks,

-theo

---

### Post by Ocxic on 2007-02-12
post your /boot/grub/menu.lst file and the output of "sudo fdisk -l" from your terminal, and your /etc/fstab, please.

the terminal is in Applications-->accesories

---

### Post by theophane.weber on 2007-02-13
Hi,

thanks for your help. This problem has been going on on three different installations of ubuntu I have had, with each time a slightly different partitioning system. In my current version, I was hoping to make it work every time by putting ubuntu in the first partition of my first disc. It was not enough... What really puzzles me is that sometimes it works, sometimes it doesn't (i would think it should either work or not, but not something in between). If I have a usb key in my screen (my monitor has two usb plugs-  it is itself connected to a usb port of the tower), it tends to bug more. If not a single USB device is used (exception of my keyboard, mouse, and external wireless "modem"), it still bugs, but not as often. Even weirder, it seems I increase the chances of booting by turning the screen off during boot (I haven't run a serious statistical study to judge if the hypothesis is true, though. it could be luck).

Right now the disk boots on vista, which then gives the choice of booting vista, xp, or ubuntu. The problem definitely does not come from vista or xp (i installed ubuntu first and it was already buggy)

-theo

---------------------------------
Here is my menu.lst:
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
# kopt=root=/dev/sda1 ro

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

title		Ubuntu, kernel 2.6.15-28-amd64-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-amd64-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-amd64-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-amd64-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-28-amd64-generic
boot

title		Ubuntu, kernel 2.6.15-26-amd64-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---------------------------------
Here is the output of sudo fdisk -l:
Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2295    18434556   83  Linux
/dev/sda2            2296        2550     2048287+  82  Linux swap / Solaris
/dev/sda3   *        2551        6374    30716280    7  HPFS/NTFS
/dev/sda4            6375       18241    95321677+   7  HPFS/NTFS

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb4               2       48641   390700800    f  W95 Ext'd (LBA)
/dev/sdb5               2       48641   390700768+   7  HPFS/NTFS

------------------
And here is the fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb5       /media/data     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda4       /media/vista    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda3       /media/xp       ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

