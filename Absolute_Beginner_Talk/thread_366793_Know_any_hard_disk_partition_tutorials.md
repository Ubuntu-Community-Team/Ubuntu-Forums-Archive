---
title: "Know any hard disk partition tutorials?"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by jonsayer on 2007-02-21
So a friend told me that the default partition editor that comes on the 6.06 install disk could destroy files on your hard drive if you don't get them all on to one side of you hard disk before you partition the drive. 

Obviously, this would suck.

Are there any good tutorials out there that would teach me how to get my disk ready for a partition?

Also, once I do partition, what do I do to run one OS or the other? Does it just give me a little menu that says "Windows XP or Ubuntu?" automatically?

And how does the "setting up a partition that both OS's can share" thing work? would I see an extra drive in "My computer" or in my file system?

---

### Post by bodhi.zazen on 2007-02-21
Well, a few comments ...

Yes, although rare, partitioning a hard drive can lead to data loss. You should already have a back up of any important data, and if you do not, now is the time to start :p

Second, as far as partitioning goes, first defragment your hard drive. There may be some files that are unmovable, and I have seen people worry about this, but it does not matter as long as the drive was defragmented.

As far as tutorials :

[http://www.ubuntuforums.org/showthread.php?t=282018](http://www.ubuntuforums.org/showthread.php?t=282018) 

Install : [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

gparted : [Documentation](http://gparted.sourceforge.net/documentation.php)

As far as a data partition goes to share data, you can use FAT without any additional installation.

For access (in Ubuntu) to ntfs :[http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)

For access (in windows) to ext3 : [http://www.fs-driver.org/](http://www.fs-driver.org/)

To mount :

> Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)[/indent][/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

HTH 8)

---

### Post by skyhopper88 on 2007-02-21
All you need to do is defrag your hd in windows first, should rearrange everything. Usually twice is recommended. I run checkdisk too, just to be safe. After you install Ubuntu, grub starts up after the bios but before any OS. It's like a dos prompt where you chose what you boot into. There are several ways to share files. 1) by setting up a swap partition (usually 2 gigs or so). It'll be FAT32, which both OSs can read/write to natively. Linux can read NTFS natively, but nor write unless you use ntfs-3g
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)
Also, I use a Ext2/3 driver to read/write to linux partitions in Windows.
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by jonsayer on 2007-02-21
what is the name of the file system both linux and windows can read and write to natively?

That is what i want my documents folder to be.

---

### Post by skyhopper88 on 2007-02-21
Fat32

---

