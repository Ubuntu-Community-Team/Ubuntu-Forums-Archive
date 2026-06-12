---
title: "Duel boot disaster?"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by nnjond on 2006-11-25
Hello, please can you help me?
I have attempted to install Dapper as a duel boot with Win 2000. 
On start-up, i am offered the option of MS, but it leads to this black screen:

[B]
Booting MS Windows
Boot 	(hd0,0)
  Filesystem type unknown, Partition type 0x 83
Savedefault
Makeactive
Chainloader +1

Error	13:	Invalid or unsupported executable format

Press any key to continue
[/B]


What has happened ? -and have i irrevocably lost the data on my primary drive.

I know  my other  data is safe on a FAT 32 partition on my slave drive but i can't read or write to it from Dapper, (Status: “inaccessible” in Disks Manager).

Also Ubuntu seems to have installed two partitions on my slave drive, (one is a swap). Why ?

---

### Post by bulldog on 2006-11-25
If you can boot Ubuntu can you give me the outcome of```
sudo fdisk -l (l as in like)
```

And your menu.lst should be nice too```
cat /boot/grub/menu.lst
```

So we can see how your disk is partitioned and how it's listed in your menu.lst.

---

### Post by louieb on 2006-11-25
Oh hello bulldog. 
nnjond, your in good hands now. his bark is worse that his bite. :]

---

### Post by nnjond on 2006-11-25
Thankyou for your interest. I think i've done what u ask. See below:


Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       10010    80405293+  83  Linux
/dev/hda2               1           1           0+  83  Linux
Partition 2 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2        8194    65810272+   f  W95 Ext'd (LBA)
/dev/hdb2   *        8195       19457    90470047+  83  Linux
/dev/hdb5               2        8018    64396521    b  W95 FAT32
/dev/hdb6            8019        8194     1413688+  82  Linux swap / Solaris

Disk /dev/sda: 1030 MB, 1030750208 bytes
16 heads, 32 sectors/track, 3932 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3932     1006576    e  W95 FAT16 (LBA)







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
# kopt=root=/dev/hdb2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title           Ubuntu, kernel 2.6.15-26-386
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hdb2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hdb2 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd1,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows 2000 Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by louieb on 2006-11-25
Yes you listed exactly what Bulldog asked for.
I hope Bulldog come rolling back through to confirm that what I see is true.
It looks like your Win 2000 install on hda1 has been destroyed. 
I see a third drive sda1 which looks like a 1 gig USB drive.

In a terminal window type:  ```
gksudo nautilus 
```See if you can browse the data on the fat partitions in hdb2. 
To be safe copy them off to the USB drive. 
Sorry to be the bearer of bad news. But I have been known to be wrong.

---

### Post by bulldog on 2006-11-26
I'm sorry,but I can't see any windows 2000 partition either.
Your first hard disk seems a little messed up with unfortunately no win200 install,but only a linux partition.

Your second hdd looks in order so you can boot Ubuntu.

I should download the gparted live cd [25MB]

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

and burn it to a cd and use this one to correct your first hdd.

Or you can just reinstall win200 on the first disk again and reinstall GRUB on the second one,the Ubuntu hdd,and make this the master boot device.
When you do it this way,you can load windows and ubuntu by GRUB or in case of troubles with GRUB you can boot win2000 direct from the first hdd by changing the boot order.

Can't make out more of it ,and I'm sorry about your win2000,I hope you didn't had important data on that hard disk. 
It's very important when you install Ubuntu to check which partitions are reformatted,so it won't reformat your windows to ext3
I think you had a mistake which hdd you should use and accidently reformatted your first hdd.

Swap is a little partition which is used when you run out of fysical memory,like the windows page file.

You can find a good link to reinstall GRUB with the live cd at the bottom of louieb's posting.

---

### Post by nnjond on 2006-11-26
Thankyou louieb and Bulldog. Am digesting your advice.

---

### Post by nnjond on 2006-11-26
Duel boot disaster pt 2.

My original goal was simply to have Win 2000 & Ubuntu on my primary, both with read & write to the same data on my slave as a staging post to full migration. The mess i'm in now is that Dapper seems to work well, but i can't get at my data (see earlier in thread)- though i could in Windows! That is my immediate problem. Do u have any advice?  i'm sorry if u have to repeat yourself.

re: gksudo nautilus: 

 root – File browser opened;  Places were:
 root; contained Desktop, 
Desktop, (empty)
file sys. Linux files.

The Terminal script replied with a gnome UI WARNING (?) Should i be revealing this content online ?

---

### Post by Bartender on 2006-11-26
I don't know much about Linux, so don't take my input too seriously.  But there are some very weird lines of text in your fdisk-l.  Never seen "Partition 2 does not end on cylinder boundary".
It appears that you installed Linux to your second hard drive too.  Look at dev/hdb2 and dev/hdb6.  dev/hdb2 has the * notation, so it's flagged as the bootable partition on the second drive.

Look at the block numbers (or whatever they're called)
/dev/hdb1 2 8194 65810272+ f W95 Ext'd (LBA)
/dev/hdb2 * 8195 19457 90470047+ 83 Linux
/dev/hdb5 2 8018 64396521 b W95 FAT32
/dev/hdb6 8019 8194 1413688+ 82 Linux swap / Solaris

You have an extended partition starting at "8194" and extending to "65810272".  Those numbers describe physical space on your second drive.  Inside that extended partition, starting at "8195", is a Linux install.
However, dev/hdb5 indicates that you have a FAT32 partition extending from 8018 to 64396521.  Starting at 8019 & extending to 8194 is a Linux swap partition.  I hope someone comes along who can read this data better than me, because I don't understand how  that's even possible.

Do you have some time on your hands, broadband, and a working PC?  I'd suggest downloading [GParted]("http://gparted.sourceforge.net/livecd.php") LiveCD and burning the download to a CD.  This can be done on a Windows PC.  You end up with a bootable CD that gives you a graphical map of your partitions.  A picture can be worth a thousand words, and I'm sure that terms like "/dev/hdb2 * 8195 19457 90470047+ 83 Linux" are just giving you a headache right now.

I've seen people post the map from GPartedLiveCD, although I don't know how they did it!  It was very helpful to see the map.  I'm pretty sure you should be able to generate 2 maps, one for each HDD.

---

### Post by bulldog on 2006-11-26
Thanks Bartender,I didn't even see this,I was looking for a win2000 install.

And you're totally right,the block numbers are messed up.
The gparted live cd should make this clearer indeed,you can make snapshots of your gparted to post on the forum.

I'm a little confused on which hdd Ubuntu is installed now.
As I look to menu list it should be on the second hdd but can't make out which is the swap and which the FAT32.

I would suggest to boot the live cd and mount your partitions one by one to see if any data can be rescued.
Then remove all the existing partitions from both drives and start from scratch.

To mount a partition from the live cd make a mount point```
sudo mkdir /mnt/rescue
```
And mount your partition one by one ```
sudo mount -t vfat /dev/hdb5 /mnt/rescue
```
If there's no recoverable data on this partition you should unmount this one and mount the next by using the correct name like hdb1 instead of hdb5.
So look at them all and see if there's any data is to rescue.

---

### Post by Bartender on 2006-11-26
Hi, Bulldog, glad to see you're back, and with new ideas.  I wrote down those directions for trying to rescue data from a partition.  In your spare time could you please make a list of all the things a person can do with the LiveCD? ;)

---

### Post by bulldog on 2006-11-26
> **Bartender said:**
> Hi, Bulldog, glad to see you're back, and with new ideas.  I wrote down those directions for trying to rescue data from a partition.  In your spare time could you please make a list of all the things a person can do with the LiveCD? ;)

You can do almost anything with the live cd,you can alter every part of your Ubuntu install on the hard disk.
The problem is to determine what you should alter and,more important,what not.:D 

I look at every problem as a single part and think in what way this can be resolved.
To make a document about the live cd and what you can do with it can cost a severe bit of time,and I'm certain I forget things to mention so I better not try.

But maybe I will make a start to see what comes out of it but no guarantees.:cool:

---

### Post by bodhi.zazen on 2006-11-26
> **Bartender said:**
> Hi, Bulldog, glad to see you're back, and with new ideas.  I wrote down those directions for trying to rescue data from a partition.  In your spare time could you please make a list of all the things a person can do with the LiveCD? ;)

Hey, that makes two of us. :p

> **bulldog said:**
> You can do almost anything with the live cd,you can alter every part of your Ubuntu install on the hard disk.
The problem is to determine what you should alter and,more important,what not.:D 

I look at every problem as a single part and think in what way this can be resolved.
To make a document about the live cd and what you can do with it can cost a severe bit of time,and I'm certain I forget things to mention so I better not try.

But maybe I will make a start to see what comes out of it but no guarantees.:cool:

Try [Knoppix Hacks](http://www.oreilly.com/catalog/knoppixhks/#top)

Most of these work with most any Live CD, although there are exceptions of course.

---

