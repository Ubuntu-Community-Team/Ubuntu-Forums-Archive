---
title: "Partition resizing problems, UNMOUNTABLE_BOOT_VOLUME"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by Saicho on 2006-10-28
Heya, I'm a ubuntu noob but a few of my friends use it so I wanted to give it a shot dualbooting Drapper Drake and Windows Media Center (I have a Dell) =(

I've installed a few different distros a few years back so I wanted to make sure my partitions were set up correctly before I started installing. The reason I went with Drapper instead of Edgy is because I have a RAID0 (two 250GB drives) and I read that dmraid doesn't work with the new kernel.

Anyways, I live booted Drapper, and installed dmraid. I went into GParted, switched it to /dev/mapper/myraidstripe and saw two primary partitions. One small FAT16 at the beginning of the drive that Dell made and the big ~465GB NTFS bootable. I gave GParted 3 things to do, 1) resize the NTFS partition to allow 20GB at the end 2) make a primary 19GB linux ext3 3) make a primary 1GB linux swap

GParted (apparently) did the first successfully, but had an error at the second. The ext3 primary was "unknown" so I told GParted to reformat to ext3, and created the swap after that (no more errors were seen here...)

The error scared me so I restarted to make sure my RAID was still okay, only to get a UNMOUNTABLE_BOOT_VOLUME in the middle of the windows startup.

I went back to the live cd, deleted both linux partitions at the end in GParted, and tried to resize the NTFS partition back to what it was. I got an error.

I tried doing it manually using ntfsresize but got also got an error "ERROR: Volume is scheduled for check. Run chkdsk /f and please try again, or see option -f."

Isn't chkdsk a windows program? I don't have an XP or a Media Center CD with me atm but I can get one and run recovery with chkdsk. Will that fix my partition problems? Does anyone have any ideas of things I should try in the meantime? The files on the windows partition are important to me so I would like to save them if at all possible. I don't know much about RAID either =(

Thanks in advance for your help, sorry for being such a noob/idiot =(

---

### Post by H.E. Pennypacker on 2006-10-29
I can't answer all questions at the moment, because the questions weren't as organized as I hoped they would be, but here it goes.

I can only comment on your Dell Media Center partition.  Before you make any permanent moves, make sure to read about some people's struggles with gettin Grub to recognize the media center partition.  Read about this to understand what may be ahead.

Also, remember what's always important: make back-ups regularly, and especially when installing or upgrading.

---

### Post by Saicho on 2006-10-29
I'm sorry about not organizing my questions very well, let me try again.

The main purpose of my post was to get advice about how to get my windows mce ntfs partition to boot again.

Some things I should note are that I haven't actually tried to install ubuntu since I couldn't get the proper partitions on my raid0.

My questions:

1. How do I go about "fixing" the NTFS parititon so at least windows can boot and/or how can I access the files from the NFTS parititon.

2. Why can't I use ntfsresize to "fix" my partition before? Why is it giving me "ERROR: Volume is scheduled for check. Run chkdsk /f and please try again, or see option -f."? Do I need to do this using a Windows Media Center Edition recovery cd?

3. Once I have the NTFS partition properly resized and propely bootable, how do I go about creating linux parititons on it (since GParted threw an error when I tried it before). Is there something I need to do to get GParted to work right with RAID or should I just be using fdisk?

---

### Post by H.E. Pennypacker on 2006-10-29
From what I am reading, it looks you have not already installed Ubuntu. Good.

1.  Use what it says.  Use chkdsk /f to fix the MBR.

[Learn more about ntfsresize here]("http://en.wikipedia.org/wiki/Ntfsresize").

2.  ntfsresize does exactly what it says.  It resizes an NTFS partition.  It doesn't fix it, and it doesn't fix the MBR either.  When using the chkdsk /f command, you will need a Windows CD.  You could probably use a spare XP or Vista CD, or whatever CD you have.  When I had an MBR problem,   I used my XP CD.  If you get to a problem with admin passwords, don't worry, its not your fault, but I won't get into this, because you may not face this problem.

The following directions, which I have not gone through thoroughly, should work:

[http://www.updatexp.com/windows-xp-chkdsk.html](http://www.updatexp.com/windows-xp-chkdsk.html)

3.  You can create the partitions using the installer that comes with Ubuntu.  Start up the Live CD, and start the installer.  Then go to the partitioning part, and opt for manual partitioning.  Then feel free to create partitions there.

Follow these instructions by AYSIU:

[Installing Ubuntu.]("http://psychocats.net/ubuntu/installing")

Let us know if you need any other help.

---

### Post by Saicho on 2006-10-30
Thanks very much for your help! I wasn't really able to fix the problem using chkdsk (said the volume was unrecoverable) but I did manage to mount the NTFS parition and copy the files I needed to an external drive. I repartitioned the way I want everything to be, reinstalled windows.

I tried to install drapper using the FakeRaid HOWTO but I can't get grub to function corretly. It stalls after stage 1.5 and says loading please wait and nothing happens.

I've searched the forums, tried a bunch of different things but I'm stumped. Here is some of my data:

Two 250GB SATA drives in software RAID0. dmraid puts my raid drive in /dev/mapper/nvidia_bafadeai

fdisk -l
```

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6       58111   466736445    7  HPFS/NTFS
/dev/sda3   *       58112       60483    19053090   83  Linux
/dev/sda4           60484       60618     1084387+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table

```

fdisk /dev/mapper/nvidia_bafadeai

```
Command (m for help): p

Disk /dev/mapper/nvidia_bafadeai: 499.9 GB, 499999997952 bytes
255 heads, 63 sectors/track, 60788 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_bafadeai1               1           5       40131   de  Dell Utility
/dev/mapper/nvidia_bafadeai2               6       58111   466736445    7  HPFS/NTFS
/dev/mapper/nvidia_bafadeai3   *       58112       60483    19053090   83  Linux
/dev/mapper/nvidia_bafadeai4           60484       60618     1084387+  82  Linux swap / Solaris

```

As you can see I have 4 primary partitions. The first one is the generic dell utility, second being the NTFS, third being linux root (bootable, containing grub files), fourth being swap.

I set grub up using:
```

grub
device (hd0) /dev/napper/nvidia_bafadeai
root (hd0, 2) #since root and grub files are on the third partition
setup (hd0)
quit

```

with no errors.

/boot/grub/menu.lst:
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
password <mypassword>
password --md5 <mypasswordhash>

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

title Windows XP
rootnoverify(hd0,1)
makeactive
chainloader +1

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
# kopt=root=/dev/mapper/nvidia_bafadeai3 ro

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
# lockalternative=true

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

title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/mapper/nvidia_bafadeai3 r$initrd          /boot/initrd.img-2.6.15-27-386

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
lock
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/mapper/nvidia_bafadeai3 r$initrd          /boot/initrd.img-2.6.15-27-386

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

```

I'm completely stumped and any help would be greatly appreciated, thanks in advance!

---

### Post by JayTee on 2006-10-30
If you boot with the LiveCD or Gparted's LiveCD (I highly recommend downloading and using it!) can you view /dev/sdb2 from Gparted and if so what partitions are listed on /dev/sdb2?

---

### Post by Saicho on 2006-10-30
Yes, I run the Drapper LiveCD. Every time I run it I also install dmraid from the universe packages.

In GParted I do not see /dev/sdb2, only /dev/sda and /dev/sdb and my /dev/mapper/myraidstuff. Both sda and sdb are completely unallocated, but...

In the FakeRAID HOWTO I was told to install dmraid and use the /dev/mapper/myraid to partition and leave /dev/sda and /dev/sdb alone. /dev/mapper/myraid is where my 4 primary partitions are. The fdisk output is shown above.

Again, any help is appreciated and thanks in advance!

---

### Post by H.E. Pennypacker on 2006-11-03
What I don't understand is why you are not doing this normal way.  It may have something to do with RAID disks, hardware that I am completely unfamiliar with.  I can only help you with the normal procedure for installing Ubuntu, from downloading and burning Ubuntu to installing it to your harddrive.

Why didn't you us[e aysiu's guide on installing Ubuntu alongside Windows?  Click here for the guide]("http://psychocats.net/ubuntu/installing").

Check out that guide, and make sure you follow it to a T.  Let us know of any subsequent problems.

---

