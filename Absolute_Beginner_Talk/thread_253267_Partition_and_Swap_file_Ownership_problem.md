---
title: "Partition and Swap file Ownership problem"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by filosofic on 2006-09-08
Cannot write to FAT32 partition created with Partion Magic in XP.
Tried various sudo chmod 777 commands in terminal but am missing something.

Computer Specs:
HP Pavilion Notebook ze5375us
2.4 Ghz 40 GB HD
XP SP2 Installed

fstab results = 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

fdisk output = 


Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1711    13743576    7  HPFS/NTFS
/dev/hda2            2947        4864    15406335    f  W95 Ext'd (LBA)
/dev/hda3            1712        2946     9920137+  83  Linux
/dev/hda5            2947        3003      457789+  82  Linux swap / Solaris
/dev/hda6            3004        4864    14948451    b  W95 FAT32

Partition table entries are not in disk order

When I reboot into Kubuntu, hda6 is unmounted and I have to remount hda6 with the following:

sudo su
cd /mnt
mkdir hda6
mount -t auto /dev/hda6 /mnt/hda6

I then have access to the files but cannot write on that disk.

Is something wrong with the partition and if so, how can I fix it?
How can I gain ownership of hda6 permenantly?

The following information outlines what I did to get to this point.

Used Partition Magic to create a 13 GB NFTS Primary drive for XP; a 14 GB FAT32 Logical drive; and a 13 GB ext3 drive for Linux.  Oritional intention was to allow computer to boot up on Boot Magic, choose XP or Linux partition and have the 14GB FAT32 partition to share between XP and Kubuntu.

First attempted to use Partition Magic to introduce Kubuntu o/s while following instructions on how to install a new o/s.  Installation failed.  The system failed to recognize the cd.
Then deleted ext3 partition.

Second attempt was to boot from cd in bios and follow Kubuntu instructions.  Created a ext3 partition from the 26 GB (13NFTS+13ext3) origional HD.
Success in installing Kubuntu.  Successful but unable to mount 14 GB FAT32 logical drive created in XP with Partition Magic.
Error message received:  “Could not mount device.  The reported error was:  mount: can't find /dev/hda1 in /etc/fstab or /etc/mtab”
Suspect errors in partition set up confirmed by:  cfdisk message of “FATAL ERROR: Bad logical partition 6: enlarged logical partitions overlap”.

Running QTParted from terminal also produced the message:
“Error: File system was not cleanly unmounted!  You should run e2fsck.  Modifying an unclean file system could cause severe corruption.”  After reading “man e2fsck” decided I know not enough to tinker with that option yet.

Reboot in XP.  Grub shows Kubuntu and XP choises.  
Fixed “autochk program not found” by returning to windows and setting XP partition as not hidden with qtparted.
Rebooted into XP and ran PartMag, and this time no errors.

---

### Post by bodhi.zazen on 2006-09-08
Change fstab to look like this:
```
proc /proc proc defaults 0 0
/dev/hda3 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 swap swap defaults 0 0
/dev/hda6 /mnt/hda6 auto user,auto 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
```

```
sudo umount /mnt/hda6
suod chown root:users /mnt/hda6
sudo chmod 777 /mnt/hda6
```

This should mount hda6 at boot and usable via users.

to test, as a user
```
mount /mnt/hda6
```
should mount hda6, user readable

---

