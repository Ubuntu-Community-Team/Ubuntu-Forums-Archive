---
title: "help for old newbie grub error 18"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by darbytwo on 2007-04-21
I have a 80 gb HD and have installed Feisty as a stand alone but I still get the Grub error 18. I have googled and read a lot about putting the /boot partition at the start of the disk but this is beyond me at the moment.

Is there anyone who would be kind enough to walk me through a possible solution.

When I sudo grub I get grub and when I type find I get file not found.

Thank you

---

### Post by yeleek on 2007-04-21
Having similar issue here :(

[http://ubuntuforums.org/showthread.php?t=417095](http://ubuntuforums.org/showthread.php?t=417095)

You can do a manual install, and select the partitions that way.  Not sure how you direct grub to install to the usb rather than internal hard disk though...

---

### Post by freebird54 on 2007-04-21
Well - there are a number of ways of solving the problem - depending on your hardware.  I gather this is an older system?  Older systems sometimes can't see the whole drive - unless they have updatable BIOS.

If you were to have a small partition at the start of the drive to run the /boot (or even easier the / (root) partition including /boot - then putting the rest as a /home partition it should get around the boot restrictions.

This would give you three partitions to create for Ubuntu - your swap - your / - and your /home.  If you could give me some details on what you would like it to do I could post a likely good setup....

EDIT:  Here is a link to an informative Grub Page 0 might help with understanding :)

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by yeleek on 2007-04-21
Not meaning to hijack this thread or anything....

But two of us with same issue - would be great to have a new to ubuntu howto.

One question - setup makes it easy to create partitions, but where should grub be installed to if you only want it to start once the usb/external disk is connected?  would it be sda1?

Thanks

---

### Post by phidia on 2007-04-21
In the grub commandline i.e. grub>
type > find /boot/grub/stage1
that command should output your boot partition. If it doesn't then you can boot from the live/install cd and choose to re-install grub. If you do get your boot partition-something like this for example (hd0,0) then type setup (hd0,0) If you get a successful setup then reboot and see how that works. You may need to type boot (hd0,0) before you can do setup. Let the thread know how that works.

About needing a how to;  [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

---

### Post by freebird54 on 2007-04-21
If you want grub to start only when a USB drive is present, then grub should be on that drive, and that drive should be set to boot first (from bios) when present.

Otherwise it will look for a non-existent partition when the drive is not there..

---

### Post by darbytwo on 2007-04-22
Thanks to all who replied. Unfortunately I`m no further on.

I used to have a 40 gb HD and insatalled several distros without problem.This drive was replaced with my current 80gb one a Seagate. I have had this error 18 problem since then and have gone back to XP.

I then decided to go wholly over to Linux, installed Feisty and have the same error 18. I have downloaded and used the Super Grub Disk to no avail.

So I have a 80gb disk with Feisty installed but am reduced to using the live CD.

I think what I need is a detailed instruction as to either reinstall Grub or how to create a small partition at the beginning of the disk.

I have tried setting the bios to LBA, Auto and Large.

Thanks again.

---

### Post by freebird54 on 2007-04-22
It sounds like most of the error 18 problems occur with the 64 bit system. Is this what you running?  I am currently tracking down the most likely causes - it seems to be related to the use of the savedefault in /boot/grub/menu.lst - on newer grubs only.  Hang in there - we'll get it!

One thing - an 80 gB is not that large - does it get mapped strangely with LBA on?  Anyway - still tracking for fixes...

---

### Post by freebird54 on 2007-04-22
Here is some more info..

```
[Error] 18 : Selected cylinder exceeds maximum supported by BIOS
    This error is returned when a read is ttempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).

So I made my system use /dev/hda3 (which is entirely below 8GB) as /boot and reinstalled grub from feisty (doing grub-install /dev/hda too) today.

Now, lets see if it happens again ...
(booted successfully by now)

```


I assume this could differ between a 40 and an 80 because the 'translation' of hte head and cylinder counts could differ considerably.  So - you need a small booting partition if this is the case.

So - starting from unallocated space, create new partition - size it to 7900Mb - File system ext3
Create new partition size is (the rest avail - 1gb) file sys ext3
Create new partition size 1 Gb file system swap

Select first partition as /  (when choosing mount points)
Select 2nd as /home
select the 3rd as swap

format all above partitions
install.

OK?

---

### Post by darbytwo on 2007-04-22
Thanks for that, I`ll give it a go. Before I do here is a shot of mycurrent setup.

---

### Post by freebird54 on 2007-04-22
Well - you could shrink the hda1, then move it further down by 7.9 Gb, then create a new Primary to boot off.  Same description to system as before.  No need to format /home in that case - if yere/s anything there you want.... (just dump anything that wasn't 'home' material after the fact)

Anyway - hope that an 'early' on the disk small partition will cure th problem.  I also suggest staying away from savedefault in menu.lst!

---

### Post by tommcd on 2007-04-22
Try to reinstall and create a /root partition about the size that freebird54 recomended, or perhaps a bit larger if needed, but 8GB should do fine. Then create a 1GB swap, and the rest home. Choose "manually edit the partition table when you get to the partitioning part of the install. Choose mount point / for root partition, file system ext3
choose swap for second paririon
choose /home for mount point of 3rd partition, file system ext3.
The other thing you could do (if this fails) is create a small (100mb) partiton at the beginning of your hard drive. Mount it as /boot, file system ext3, and install grub to that .

---

### Post by yeleek on 2007-04-22
Having same problem as darbytwo (except i have 40gb external).  Created following partitions

/boot ext3 100mb
swap swap 2000mb
/ ext3 36000mb

At the final part of livecd install clicked advanced and told install to load boot loader to /dev/sda (removed power to internal hdd to make sure i don't wipe by mistake).  Setup gone through fine, reboot however and nothing.

Load livecd, and tell it to boot from first hdd and get the following error

'Booting from local disk...

Isolinux: disk error 01, ax=201, drive 80'

Any thoughts? read else where for earlier versions that to get this to work from external usb you had to alter the modules file to make sure usb support is loaded during ubuntu startup.  That cause the above?  or red herring?

Thanks

---

### Post by darbytwo on 2007-04-22
It works.

Screenshot and heartfelt thanks

---

### Post by yeleek on 2007-04-23
freebird54,

Thanks - to answer your question.  Its about a year old pc, a8n-sli mother board, 2gb ram, amd 4800 cpu, 7900gtx and 400gb internal sata drive.  Up until now i've been removing the power from the internal disk when installing ubuntu to the external.  Rebooting with only the external attached and it gets past POST and then just sits there.  Boot off livecd and then have it boot off first hdd (still with internal disconnected) and i get the isolinux error.

Thanks

Ben

---

### Post by freebird54 on 2007-04-23
Highly unlikely that it is the same problem then - despite the same error number.  What are the boot order settings in your BIOS?  Is the external recognized properly (both with and without the internal connected)?  There is something going on with that I think...

That isolinux error is something I hadn't seen since the days when I used to format a PC hard drive from debug, with g=c800:5 !!

---

### Post by yeleek on 2007-04-23
Hi,

I had to do a diskpart clean on the external disk so the machine would boot with it connected (post my ubuntu install attempt) but yeah machine will boot with them both connected.  And originally when i just let ubuntu perform a guided disk configuration to the external usb it did work with both rebooting, just i then got that grub 18 error.  

Is it me, am i just doing something wrong with the install?  or could it be this disk?  its a 2.5 40gb fujitsu in an external enclosure.

Thanks

---

### Post by freebird54 on 2007-04-23
One possible fix is apparently to blank out the MBR and try the install again. Here is a command that will blank out the MBR: 

```
dd if=/dev/zero of=/dev/**hda** bs=512 count=1
```

Note that this refers to the hard drive as hda.  If it is connected by >>USB it is more likely to be sda.  So  - before doing this, please post the result of:

```
sudo fdisk -l
```

from the LIve CD.  Is it possible that this HD had a life in some other place than your enclosure?  I gather that Win systems sometimes lied to the BIOS about the real configuration - but LInux won't recognize them that way....

---

### Post by yeleek on 2007-04-23
heres the result
Thanks


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         574     4610623+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *         575       48641   386098177+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40007761408 bytes
64 heads, 32 sectors/track, 38154 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

Disk /dev/sdb doesn't contain a valid partition table

---

### Post by freebird54 on 2007-04-23
Ok - so the command becomes:

```
dd if=/dev/zero of=/dev/sdb bs=512 count=1
```

Then run System->Administration->Gnome Partition Editor to create a setup beforehand - just to be sure it will!  After that an install should proceed troublefree (assuming the partitions take).

Good luck!

---

### Post by yeleek on 2007-04-23
> **freebird54 said:**
> Ok - so the command becomes:

```
dd if=/dev/zero of=/dev/sdb bs=512 count=1
```

Then run System->Administration->Gnome Partition Editor to create a setup beforehand - just to be sure it will!  After that an install should proceed troublefree (assuming the partitions take).

Good luck!

Hi,

Did that - created a partition on the drive and applied.  Went through fine.

So if i delete that partition now, run setup and create

/boot ext3 100mb
swap swap 2000mb
/ ext3 36000mb

and then tell the bootloader at the end of setup to load on /dev/sdb should that work?

THanks for all the help

---

### Post by freebird54 on 2007-04-23
Looks fine to me.  Probably don't even need to bother with a separate /boot now - that problem would be for an older machine.  Perhaps :

/ 10,000
swap 1,000
/home the rest

would be a better choice?  simpler to work with anyway - and easy to back up.

Enjoy your Feisty!

---

### Post by yeleek on 2007-04-23
Hi,

Got further - getting a grub error 14 now.  I had the boot loader install /dev/sdb

fdisk gives this

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         574     4610623+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *         575       48641   386098177+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40007761408 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1216     9767488+  83  Linux
/dev/sdb2            1217        1459     1951897+  82  Linux swap / Solaris
/dev/sdb3            1460        4863    27342630   83  Linux
ubuntu@ubuntu:~$ 

And heres my grub menu file  -  Can you advise at all please?

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
# kopt=root=UUID=50075069-5b3b-435f-ab2a-64e09a4cf073 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=50075069-5b3b-435f-ab2a-64e09a4cf073 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=50075069-5b3b-435f-ab2a-64e09a4cf073 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
chainloader	+1

```

---

### Post by freebird54 on 2007-04-23
Hmm - not seen that one before. Here is a listing entry for it.


```
14 : Filesystem compatibility error, cannot read whole file
    Some of the filesystem reading code in GRUB has limits on the length of the files it can read. This error is returned when the user runs into such a limit. 
```

I have no idea what could cause that one!  Do the Win boots work OK?  I'll have to go looking again....

---

### Post by yeleek on 2007-04-23
Yeah windows is booting fine...

I know there use to be an 8gb limit on primary partition sizes...  Could it be that and this external usb?

Wonder if it would be worth trying with say a 7.5gb /

Thanks :)

---

### Post by freebird54 on 2007-04-23
Have you tried the different kernels?  COUld be that one of them has a read error that causes it to read past end of file.... (shudder)

---

### Post by yeleek on 2007-04-23
Don't know what to do re trying other kernels...

Just tried it again, this time with a guided install leaving my main disk plugged in.  Setup went through - boot loader on sdb.  Now getting grub error 2... :( 

Wonder if there is something wrong with this disk now...  error 2 seems to relate to that.  I've been using the gnome partition admin tool to delete partitions etc.  Is there a command to completely wipe this disk and prepare it for ubuntu.  If so will try once more...

Thank you for your help regardless.

---

### Post by freebird54 on 2007-04-23
Well - that is not very good news!  The entries I've seen so far suggest that either the drive is no good - or that your system power supply is overloaded and failing.  I suspect the drive this time!

It seems to me that you are getting the equivalentof the old 'Track 0 bad' error, that preceded binning the offending disk :(

Last resort (if you feel like it) is to try partitioning/formatting with Windows (erk) and see what errors it comes up with -but the results are unlikely to be wonderful there either.  How old *IS* this drive anyway?  40's were so 2000 :) (I've still got 2)

---

### Post by freebird54 on 2007-04-23
Here's a link with all the errors you can get.  Maybe you're trying to see them all? (bad joke)  Anyway - thought you might be interested in acquiring some (hopefully) never again used knowledge....

[http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)

---

### Post by yeleek on 2007-04-23
Think i'm gonna give up then mate....  Won't bother with an external disk at all.  Maybe i might repartition internal disk to allow for ubuntu.

For now i'll leave it.

Thank you for all your help anyway

Cheers

Ben

---

### Post by freebird54 on 2007-04-23
Sorry we couldn't track down a fix - but then hardware fixes are tough over the net!  G'day to you - and hope you get things going again...

---

### Post by yeleek on 2007-04-23
Hey,

Thought i'd let you know.  Its not the HDD,  Its GRUB.

I followed the instructions for 6.10 from here [http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610](http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610) just making it a 750 partition and its working fine.  I'm actually writing this via it.  So must be some combo of that disk (maybe my mb) and grub.

Thanks for your help

---

### Post by freebird54 on 2007-04-23
Perhaps something in the way it is presented to the system through the USB.  VERY weird.  I though we tried a small boot partition though??  Oh well - glad you got it to go!  Enjoy...

---

