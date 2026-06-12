---
title: "make a new drive an extension of a directory  from another drive?"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by nipar on 2007-12-14
I have been reading all the posts i could find about the subject of mounting drives, but I am left a little confused about one thing. Is it possible to add a new harddrive, then mount it as an extension of a directory on an existing harddrive.
for example:
drive 1 is the boot drive and has a directory of /shared/videos
drive 2 is added, as directory of /shared/pictures

when browsing the filesystem, would both videos and pictures appear as subdirectories of /shared???

Also, being very new to this os, how would i mount the second drive to accomplish the directory extension.

Thanks in advance for the help :)

---

### Post by Keith Hedger on 2007-12-14
the basic syntax is :
mount -t SOMETYPE /dev/SOMTHING /PATH/TO/A/MOUNT/POINT

where  SOMETYPE is the filesystem type,  SOMTHING is the device node, or you can use a uuid or a label and /PATH/TO/A/MOUNT/POINT is just a path to an empty folder,so if i understand you yes you can mount your disk anywhere you want.

---

### Post by ctyc on 2007-12-14
Yes you simple format the new drive(ext3 for example) and them mount it as /shared/pictures

Your /etc/fstab would look in part like so:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=1dc0c90    /         ext3    defaults,errors=remount-ro 0   1
# /dev/sda2
UUID=3660adcf    /boot      ext3    defaults        0   2
# /dev/sda6
UUID=83e63934    /home      ext3    defaults        0   2
# /dev/sda5
UUID=4e8476c6   none       swap    sw              0   0

# /dev/NEWDRIVE
UUID=3660adcf    /shared/pictures     ext3    defaults        0   2

Make sure the DIR /shared/pictures exists as a mont point on your filesystem before you mount it.

Good Luck

---

### Post by HermanAB on 2007-12-14
It is also possible, by using the logical volume manager, to make one directory span several drives.

---

### Post by nipar on 2007-12-15
thanks so much, worked like a charm, until i rebooted lol :P

I used gparted to create a partition and format ext3. Now i can only mount it after the desktop loads.

error is bad magic block, fs is not ext2. Is what gparted does to the drive not compatible to ubuntu 7.1???  should i use another utility to format the drive?

---

### Post by Keith Hedger on 2007-12-15
if u have formated the drive as ext3 and u specify ext2 in the fstab u that may be giving u the problem, check that the file types match, u can also use -t auto as the file type to mount (but it doesn't always get it right)

---

### Post by nipar on 2007-12-15
here's the info i gathered. havent got the exact error message copied yet.

ran fsck.ext3 with the same error.

```
fdisk -l

Disk /dev/sda: 9099 MB, 9099542528 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb83b62bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1053     8458191   83  Linux
/dev/sda2            1054        1106      425722+   5  Extended
/dev/sda5            1054        1106      425691   82  Linux swap / Solaris

Disk /dev/sdb: 18.3 GB, 18389272576 bytes
255 heads, 63 sectors/track, 2235 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b7b65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2235    17952606   83  Linux


fsck from terminal after desktop loaded:

fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sdb1: clean, 12/2244608 files, 114501/4488151 blocks


fstab---------------

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1574131e-ec75-4b57-ba01-3940e928ea8b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=2cfbb4c2-5e9a-433f-8a35-ef697f9b8c11 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdb1    /osdrivers/devices ext3 defaults,errors=remount-ro 0 1
```

/osdrivers/devices does exit on boot drive.
also tried to run e2fsck with same error, magic block superblock error.
!! should i try to format it again with something other than gparted?

---

### Post by nipar on 2007-12-15
to make things worse, now sometimes my 8 gig boot drive which should be sda is being mounted as sdb and  my 18 gig is being mounted as sda if i add the following line to fstab:

/dev/sdb1    /osdrivers/devices ext3 defaults,errors=remount-ro 0 1

i think perhaps i should mount it to /media/sdb1 and share folder from it. what do you think??

changed line in fstab to:

/dev/sdb1    /media/sdb1  ext3 defaults,errors=remount-ro 0 1

created /media/sdb1 directory and when rebooted got the following error:

Log of fsck -C -R -A -a 
Sat Dec 15 15:53:36 2007

fsck 1.40.2 (12-Jul-2007)
fsck.ext3: No such file or directory while trying to open /dev/sdb1

/dev/sdb1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

---

### Post by nipar on 2007-12-15
ok... i seem to have solved the problem by finding the uuid of the partition on the 18 gig and forcing fstab to mount the 18 gig with it. Now all my errors are gone :guitar::popcorn::)

Is this a common problem with ubuntu 7.1, that adding lines to fstab using /dev/sdx causes problems??

---

### Post by Keith Hedger on 2007-12-16
i have had some problems with gparted and formating a drive, it just would not format and partition my ipod so i used fdisk in interactive mode to set the partitions and mkfs to format them, i also have noticed that since upgrading to feisty the /dev/XXX would occasionaly change on my external drives so i switched to using uuids  which seem to work ok, the onlly gotcha with uuids is that they change on format, any way glad u solved your prob:)

---

### Post by nipar on 2007-12-17
My thanks to Keith and all who helped. :D  After my experiences with OpenSUSE and PCBSD I am very happy to find Ubuntu and the user support is definitely FIRST CLASS!

I guess i'll have to learn about fdisk more, tho the fdisk --help didnt give me much to work with.

And mkfs i havent even touched yet. I'll dive into the man files shortly and see what kind of mess i can make :lolflag:.

Thanks again to all.

---

### Post by Keith Hedger on 2007-12-17
no problem we all have to start somewhere i posted some real dumb questions here when i first switched to linux!
try this:
[http://www.vnunet.com/personal-computer-world/features/2166563/keep-music-playing](http://www.vnunet.com/personal-computer-world/features/2166563/keep-music-playing)
it is really a howto for updating an ipods firmware but it will show you how to use fdisk on page 2 (its actually easier to use in interactive mode :confused: )

---

### Post by jaybombalous on 2007-12-17
U may wanna check out 'persistent block device naming'. It explains why u need to use the UUID of the drive. 

Your OS, ubuntu, picks up the order of the disk from the bios. The bios selects these disk as they see them and in what order the bios boots the drives.

In other words, if u have two drives in the computer and each one has a bootable partition, which ever disk is being booted the bios will flag this as the first block device /dev/xxa then b and c and so on and so forth.

This can cause a lot of problems when u hard code a file like fstab to mount sdb5 when there is no sdb5 because its really being registered as sda5 because the bios swapped the drives on boot. To solve this u use 'persistent block device naming' conventions.

click here for details and for a better grasp  [http://wiki.archlinux.org/index.php/Persistent_block_device_naming](http://wiki.archlinux.org/index.php/Persistent_block_device_naming)

---

### Post by nipar on 2007-12-17
Thanks Keith, but I didnt see much in that article about fdisk-interactive. I will look into it further.

Ok Jay. This might complicate things further...lol.
I have 2 scsi cards installed in the computer. Card 1 was an adpatec ultra160 and Card 2 was an IBM ServeRAID-4L which also runs at Ultra160. I found that I need to switch the order of the cards in the computer by pulling them and installing the IBM card in slot 4, Adaptec card in slot 5 and disabling the scsi bios on the Adaptec card. That solved the boot order problem as far as the computer's bios was concerned.

The IBM card is running 2 x 9gig scsi ultra160 drives mirrored, as boot drive and os.

An 18 gig scsi ultra160 drive is attached to the adaptec card with the data on it.

In this configuration I can add more drives easily with max throughput for fileserving.

Even setup like this, so the bios sees the drives in the order i want, mounting drives and/or partitions was a problem with "/dev/sdx" lines in fstab. Every 2 or 3 reboots would see the 18gig mouted as "/dev/sda/" when it should be "/dev/sdb".
Digging around in the /dev directory I stumbled upon the UUID files for all the drives and then configured fstab for UUID, problems were all solved.
Now, I am not well versed in Linux of any flavor, so I dont know if that setup is part of the problem or if it's a "bug" or unaddressed known issue with Ubuntu. I will leave that judgement to those of you with much experience.

---

