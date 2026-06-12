---
title: "Problem installing windows"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by NorthernPaladin on 2007-07-21
My problem is this: I wanted to test ubuntu again and deleted windows partition, and installed feisty to it. Then I used ubuntu for few days and decided to go back to windows. When I put the windows cd in, it started to install normally, but when it get to the point where it should boot first time from the hard-drive it froze. Then I tried again to install windows, same result. Tried another cd, same result. Then I installed feisty to test, deleted my windows partition and put feisty on there. It installed normally but now when I boot my computer there is a menu to start either windows or ubuntu, but I dont have windows, I installed feisty to that partition. My friend thinks there is some problem with MBR, so how do I repair it(because I need windows for some stuff)? Sorry if this is in the wrong section, feel free to move it to the right one.

---

### Post by thefoolisme on 2007-07-21
To fix the MBR for Windows,  boot from the installation CD and use a tool named Recovery Console. The fixboot and fixmbr commands would restore the boot sector and the master boot record (MBR) so that the machine would boot directly into Windows again.

---

### Post by rolfen on 2007-07-21
can you format your hard drive and start over? or do you have any data on other partitions?

---

### Post by NorthernPaladin on 2007-07-21
I have about 60GB in the other partitions but I borrowed a usb hard-drive from a friend so I can copy everything and format the whole drive. So should I do that?

EDIT: how do I format the usb drive to fat32 in ubuntu?

---

### Post by thefoolisme on 2007-07-21
> **NorthernPaladin said:**
> I have about 60GB in the other partitions but I borrowed a usb hard-drive from a friend so I can copy everything and format the whole drive. So should I do that?

EDIT: how do I format the usb drive to fat32 in ubuntu?

If you have the USB hard drive, then I would back up your stuff, and format.  Would probably take less time, ultimately.  

Once the USB drive is mounted, I would think you could use gparted to change the format of the USB drive.  If it's not already installed in your ubuntu setup, you can get it from Synaptic.  Works like partition magic for windows. 

If the USB hard drive is in NTFS, you should be able to access it in Ubuntu with ntfs-3g, also available from Synaptic.

---

### Post by nitro_n2o on 2007-07-21
> **NorthernPaladin said:**
> I have about 60GB in the other partitions but I borrowed a usb hard-drive from a friend so I can copy everything and format the whole drive. So should I do that?

EDIT: how do I format the usb drive to fat32 in ubuntu?

To format your drive first unmount it 
sudo unmount /dev/sda    make sure the name is right .. it might be sdb or sda2 or whatever 
then: 
sudo mkfs.vfat -l /dev/sda again make sure the name is right

---

### Post by NorthernPaladin on 2007-07-22
Tried the recovery console and fixmbr. It said something that the mbr was invalid and asked if I want to continue, I pressed yes, then it said that it wrote successfully  new mbr but when I tried it would not boot into windows.

---

### Post by kirios on 2007-07-22
[B][COLOR="Sienna"]Could you post the output of 
```
sudo fdisk -l
``` and the contents of /etc/fstab?[/COLOR][/B]

---

### Post by NorthernPaladin on 2007-07-22
```
sudo fdisk -l
``` 
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2        1912    15350107+   f  W95 Ext'd (LBA)
/dev/hda2   *        1913        9728    62781988+   7  HPFS/NTFS
/dev/hda5               2         766     6144831    b  W95 FAT32
/dev/hda6            1710        1912     1630566   82  Linux swap / Solaris
/dev/hda7             767        1709     7574616   83  Linux

Partition table entries are not in disk order


/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda7
UUID=62d5356c-6393-464a-9654-53d644ae5dc4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=ACB452D8B452A51C /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=F4C4-7C3B  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=6149cd41-f580-416b-930f-2106eee7f81e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by kirios on 2007-07-22
> Then I installed feisty to test, deleted my windows partition and put feisty on there. It installed normally but now when I boot my computer there is a menu to start either windows or ubuntu, but I dont have windows, I installed feisty to that partition. 
[COLOR="DarkRed"]I'm assuming /dev/hda2 still holds your Windows system since you seem to have reinstalled Feisty to /dev/hda7. If that's so, you may still be able to rescue Windows. What does your /boot/grub/menu.lst look like? 
Btw if your USB disk is empty, format it to FAT32 with gparted and back up your data files from /dev/hda5 first. Just in case. :-)[/COLOR]

---

### Post by NorthernPaladin on 2007-07-22
> **kirios said:**
> [COLOR="DarkRed"]I'm assuming /dev/hda2 still holds your Windows system since you seem to have reinstalled Feisty to /dev/hda7. If that's so, you may still be able to rescue Windows. What does your /boot/grub/menu.lst look like? 
Btw if your USB disk is empty, format it to FAT32 with gparted and back up your data files from /dev/hda5 first. Just in case. :-)[/COLOR]
 Well, there is windows partition, I tried to install it again and deleted the ubuntu partition, used part of it for windows and then installed feisty to remaining space. Now the problem is that I cant do anything to the usb drive, it says I do not have required rights to anything, even if I try sudo nautilus. Any tips?

EDIT: the format of the usb drive is fat32

---

### Post by NorthernPaladin on 2007-07-22
boot/grub/menu.lst



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
# kopt=root=UUID=62d5356c-6393-464a-9654-53d644ae5dc4 ro

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
# defoptions=quiet splash locale=fi_FI

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
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=62d5356c-6393-464a-9654-53d644ae5dc4 ro quiet splash locale=fi_FI
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=62d5356c-6393-464a-9654-53d644ae5dc4 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by kirios on 2007-07-22
[COLOR="DarkRed"]So Windows is apparently still on your hard drive and also available in the grub menu. 

Can you see the files on the Windows partition?

What happens when you boot the PC and select the Windows option?[/COLOR]

---

### Post by NorthernPaladin on 2007-07-22
it just hangs up where it should boot

---

### Post by kirios on 2007-07-22
[COLOR="Sienna"]Sounds like a Windows problem. Sometimes the easiest way is to delete all the partitions (with the gparted CD for example) and just start over again.[/COLOR]

> Now the problem is that I cant do anything to the usb drive, it says I do not have required rights to anything, even if I try sudo nautilus. Any tips?
[COLOR="Sienna"]Use **mount** to find out where your USB drive is mounted (for example, /media/disk), then **ls -l /media** to check the permissions on /media/disk.[/COLOR]

---

