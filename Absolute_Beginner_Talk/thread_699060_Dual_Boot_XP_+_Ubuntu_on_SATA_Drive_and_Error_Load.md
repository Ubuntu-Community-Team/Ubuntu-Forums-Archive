---
title: "Dual Boot XP + Ubuntu on SATA Drive and Error Loading OS"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by golbez_88rule on 2008-02-17
Hello everyone, I have been using Ubuntu for over a year on my laptop (dual boot XP and Ubuntu 7.10) and it has worked very well.  Yesterday I installed Ubuntu 7.10 on my PC which already had Windows XP installed first.  I have one serial ATA hard drive which has the windows and linux installations, and an IDE hard drive that serves as data storage.  Before installing Ubuntu, I freed up about 30 GB space after the WinXP partion of the SATA disk to hold the linux os.  During the installation process, I chose the option "Use largest remaining available space" in the partitioning step.  During the installation process I did not get any message about XP being detected as already on the hard drive.  I suspect that is because GRUB was defaulted to be installed on the IDE disk instead of the SATA disk.    After the installation was complete and rebooted the system, I got the dreaded "Error loading operating system" message, no GRUB menu at all.

  
If I use the Live CD during the boot up process and then choose "Boot from hard disk" I am able to see the GRUB menu, and I am able to boot into XP and Ubuntu just fine from the menu.  However I do not want to have to use the Live CD to get into either OS.  After doing more research on the forums, I saw some posts that recommended having an IDE drive unplugged before installing Ubuntu on a SATA drive, since that would force GRUB to install onto the SATA drive.  I wish I had done that research sooner, but because the installation onto my laptop went so well I did not think to do that before trying to install it on my PC.  I have attached two screen captures of the partition editor application for both hard drives (hda is the backup IDE drive and sda is the SATA drive with XP and Ubuntu).  I notice that now my IDE drive has a bootable flag, and I honestly am not sure if it was bootable before this installation.  In the BIOS, the boot order is Floppy, CD-ROM, Serial ATA.  Here is some more information about my system (device.map, menu.lst, fstab, fdisk)

[IMG]http://i5.photobucket.com/albums/y186/sheed03/Screenshot--dev-hda-GParted.png[/IMG]
[IMG]http://i5.photobucket.com/albums/y186/sheed03/Screenshot--dev-sda-GParted.png[/IMG]

output from device.map:
```

ubuntu@ubuntu:/$ cat /mnt/rescue/boot/grub/device.map
(hd0)   /dev/hda
(hd1)   /dev/sda
```

output from grub's menu.lst:

```

ubuntu@ubuntu:/$ cat /mnt/rescue/boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=b1131ad9-73b7-4d78-9b9f-516c8d0d10ad ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b1131ad9-73b7-4d78-9b9f-516c8d0d10ad ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b1131ad9-73b7-4d78-9b9f-516c8d0d10ad ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
```

output from fdisk -l:

```
eric@Abit:~$ sudo fdisk -l
[sudo] password for eric:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5d52c4ad

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           2       19457   156280320    f  W95 Ext'd (LBA)
/dev/hda5               2         638     5116671    7  HPFS/NTFS
/dev/hda6             639       19457   151163586    7  HPFS/NTFS

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f9c0f9c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            6212       20023   110944890    f  W95 Ext'd (LBA)
/dev/sda3            2551        6211    29406982+  83  Linux
/dev/sda5            6375        7649    10241406    7  HPFS/NTFS
/dev/sda6            7650       20023    99394123+   7  HPFS/NTFS
/dev/sda7            6212        6374     1309234+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

output from find /boot/grub/stage1 in grub:

 ```
      [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd1,2)

grub> 
```

My question: Is there a way to "move" the GRUB location from the IDE drive to the SATA drive, if in fact it was installed on the IDE drive?

---

### Post by agim on 2008-02-17
Use the livecd to set up your mbr. Read a few of the posts, don't just use the first commands you see. 
[http://ubuntuforums.org/showthread.php?p=4346336#post4346336](http://ubuntuforums.org/showthread.php?p=4346336#post4346336)

Good luck!


Edit: Thank link will lead you to another link... just follow along. Sorry about that.
Also, look into getting the super grub disk. I have had to use that before, its a great tool.

---

### Post by golbez_88rule on 2008-02-17
agim, thank you very much for your help.  I have a couple of questions regarding the solution in the post you referred me to:

I have gone into the grub shell and I received the following for "find stage 1"

```
grub> find /boot/grub/stage1
 (hd1,2)
```

In my current menu.lst file, I see the following section:

```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)
```

Since (hd1) corresponds to the /dev/sda drive (which is my current sata disk with XP and Ubuntu installed), it seems like the default grub root device is in the correct place ???   I  will download the super grub cd tonight, it sounds like a very useful tool.

---

### Post by agim on 2008-02-17
yeah, it looks like its in the right place. The last line, the line with only one #. Erase that and save the new version, without the #. This should allow it to boot.

Glad to help, welcome to the forums! Most answers are just a google or a forum search away. When you get more comfortable with searching you will see that answers are everywhere.

Edit: I feel a little sheepish saying this, but to thank someone, push the little blue ribbon underneath their post.

---

### Post by golbez_88rule on 2008-02-17
Thank you very much agim.  I feel embarrassed that I've done so much programming in languages like perl, mysql, php, vb and I did not realize that I could just uncomment that line!!!  I will try that now and see what happens.

After uncommenting the line, the system now just boots into XP straight without any grub menu.  It seems that the MBR was never touched, so I will make a backup of the MBR and then proceed to install GRUB.

---

