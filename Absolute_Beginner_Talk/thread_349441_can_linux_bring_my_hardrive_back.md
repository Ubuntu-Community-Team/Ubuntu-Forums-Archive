---
title: "can linux bring my hardrive back ?"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by dumbalien on 2007-01-30
Hi all,

The other day i switched my computer on and i would not boot into xp. I disconnected my secondary hardrive that stores all my personal info, and it worked. Everytime i try and boot up with the second hardrive connected i get the problem.

I have got the ubuntu liveCD and wondered if there is a way to retrieve the files through ubuntu?

I am  a complete ubuntu newbie. But am very willing to learn, and may become a convert.


thanks in advance

---

### Post by kb3hkg on 2007-01-30
Sounds like a possible problem either with boot sector or just the MBR. So long as you can boot linux with the drive plugged in you should be able to use the mount command and then be able to access the disk. Do you need further help with this command?

---

### Post by kebes on 2007-01-30
Yes, it should be possible to use the Ubuntu LiveCD to mount the screwy hard-drive and copy the files somewhere else. (Of course, if the hard-drive is totally dead this won't work.)

You said you have the LiveCD, so the next thing to try is to go into your BIOS, set "boot from CD-ROM" and bootup the computer with the LiveCD.

Once there, you're going to have to "mount" your hard drives, and then you'll be able to copy files from one hard-drive to the other.

A quick guide to "mounting" can be found here:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only)


However if that guide doesn't make sense, feel free to post here and we'll talk you through the steps required.

---

### Post by NESFreak on 2007-01-30
can it be a master/slave issue or that your systems 2nd hard disk also has an active boot section?

NESFreak

---

### Post by dumbalien on 2007-01-30
Thanks for the quick replies :D 

will have a look at the thread.

---

### Post by scbonney on 2007-01-30
I had a similar problem when trying to install ubuntu with win 2000, dual boot, two hard drives.  I finally disconnected the ubuntu for a bit, used a windows boot disk to boot windows, copied my files to a cd.  I had to reinstall ubuntu because of grub problems trying to dual boot.  I now have the win 2000 drive disconnected and ubuntu as master.

May be this will help.  Its not the solution someone who knows linux would use but it helped me.

---

### Post by podunk on 2007-01-30
It depends on your hard drive. If it's gone bad mechanically you'll most likely have to send it to a data recovery company. If it's just starting  to go bad or if Windows just lost it's mind or a driver there is a very good chance you can get your data.

This is much easier with a USB external drive than copying to CD or DVD. You'll need some very basic computer knowledge - how to identify your drive and and file system type, stuff like that.

Boot up in windows and format your USB drive to the fat32 file system *not* NTFS. Power down and unplug the USB drive.

Boot up into Ubuntu and plug in your USB drive, it should automount.

Start the terminal. Applications >Accessories>Terminal. When you're new it's a lot easier to copy and paste than type in stuff - but you don't learn anything.

First see if the drive is seen by Ubuntu:

```
 sudo fdisk -l
```

note that is the lower case L in the command, not 1. Linux is case sensitive - Cat is not the same as cat.

You will see an output something along the lines:
> 
Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         583        8938    67119570    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/hdb: 92.6 GB, 92641812480 bytes
255 heads, 63 sectors/track, 11263 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2816    22619488+   c  W95 FAT32 (LBA)


Disks are listed like this in Linux:
**hda** is your primary boot drive 
**hdb** is the second drive  on the computer, and it sounds like this is the one you want to copy.

If it sees the drive in fdisk - there is hope. :)

```
df -h
```

The output will have something along these lines:
> /dev/hdb1 116G  3.2G  107G   3%  /temp/disks-conf-hdb1 

The last column shows where in your file system your hard drive is mounted. Using the live CD it will be somewhere in the folder /temp on mine it is /temp/disks-conf-hdb1

Type
```
gksu nautilus
```

At the top of the terminal is 
File>Open Terminal    - click this and type it again in the new terminal that opens:
```
gksu nautilus
```

This will open 2 file browsers with super user permissions.

Use one file browser to navigate to your hard drive. Does it see the folders? files? Yes?

Use the second file browser to navigate to the USB drive.

Right click the folder and chose copy, go to the USB drive and select paste. Continue until finished.

If you do not have a USB drive I ***think*** you can put a Cd in and it will mount it and give you a chance to format it - I don't have any blanks to remind me, sorry.

If your drive is not picked up by fdisk or df-h, then you have a damaged drive. You might try this:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
which is a windows program and will have the look and feel you are used to.

Or for a Linux recovery try this:
[www.partimage.org](www.partimage.org)

---

### Post by dumbalien on 2007-02-02
Managed to finally boot up the livecd.

Followed the quick guide for mounting. Got the hd content to show up, but all the folders had padlocks !!

closed and re-launched nautilus with gksu and now the folder that i mounted the hd shows up with a padlock, and does not let me open it.

Any ideas ??

thanks

---

