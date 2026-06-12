---
title: "cannot use all my Gigs"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by cwrann on 2007-12-29
I have just done a lot of deleting and moving around of files on a large hard drive partition.
When I view the properties of the This large partition it tells me that the contents equal 204 gb and the partition size is 216 gb but that only 3 mb is available.
I am using a ext 3 file system. Do I need to defragment or clean up the hard drive somehow to free up  this memory?

---

### Post by SOULRiDER on 2007-12-29
Defragmenting is not necessary on EXT3 partitions. Some of that space may be taken up by the journal, but i doubt its 12 GB. Have you emptied your trash?

Paste the output of
```
df -h
```

---

### Post by irish_flu on 2007-12-29
Any chance you put them in the "trash" and forgot to empty it?  I've pulled that one before....

---

### Post by Furat on 2007-12-29
Try to run fsck to check if u have any errors in your disk

---

### Post by cwrann on 2007-12-30
Thanks for the suggestions but the trash has been emptied. I went to run FSCk and got this warning.

```
WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

```

---

### Post by clayt0njknight on 2007-12-30
That's one nasty looking error.  EXT2 and EXT3 partitions don't have the option to defragment that i know of, since defragmentation is not necessary (the reason they are far superior filesystems vs windows' NTFS or even FAT).  Have you thought of backing up your data and reinstalling?  I hate to say that, but it's the "simple" fix for a 'severely damaged filesystem' as described by the error you got.  

anyone know if you can 'repair permissions on a disk' as with OS X or is that an HFS (Apple Partition Scheme)-exclusive feature?

---

### Post by taurus on 2007-12-30
You need to run fsck from the LiveCD since you can't scan the partition that you are currently using.

---

### Post by SOULRiDER on 2007-12-30
If youre gonna run fsck do it from a live CD.

---

### Post by cwrann on 2007-12-30
I have rebooted my computer since this problem has occurred so FSCK should have been performed upon reboot so I don't think it is a disk error.

---

### Post by SOULRiDER on 2007-12-30
Defragmenting is not necessary on EXT3 partitions. Some of that space may be taken up by the journal, but i doubt its 12 GB. **Have you emptied your trash?**
Paste the output of
```
df -h
```

You could also use the Disk Usage Analyzer in the System tools menu to see where all the space is going.

---

### Post by cwrann on 2007-12-30
The ubuntu OS is not installed on this partition. Can I safely unmount the partition and then FSCK it and then remount it without losing the partitions contents.
Also I think that the warning that appears is a generic warning when running the fsck command. Can anybody verify that this is a generic warning or does it only apply to corrupt file systems.

---

### Post by cwrann on 2007-12-30
Sorry that I never posted the results of the original response to my query.

SDA 2 is the partition in question.

```
home@home-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             122G   16G  100G  14% /
varrun                3.0G  112K  3.0G   1% /var/run
varlock               3.0G     0  3.0G   0% /var/lock
udev                  3.0G   64K  3.0G   1% /dev
devshm                3.0G     0  3.0G   0% /dev/shm
lrm                   3.0G   38M  2.9G   2% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1             121G   15G  100G  14% /media/sda1
/dev/sda2             217G  206G  3.1M 100% /media/sda2

```

---

### Post by cwrann on 2007-12-30
SDA 3 is what my ubuntu OS is Mounted on and SDA1 is another storage partition.

---

### Post by SOULRiDER on 2007-12-30
I strongly suggest you use the Disk Usage Analyzer app before running any fscks or any of those things.

---

### Post by cwrann on 2007-12-30
The disk usage analyzer tells me that SDA 2 is 100% used up by by the one folder (other than "lost and found" and "trash") that is on that partition.

It says that it is 100% but that the space taken up is 205 gigs.

Essentialy this is telling me the same thing that properties tells me. I am currently backing up the files that I have on this partition so that I can unmount it and run fsck. Only 45 hours to go.

---

### Post by cwrann on 2007-12-30
...And the trash folder contains 16 mb of data and the lost + found folder contains 16 mb of data.

And now that I look at my out put from df -h I am missing 6 gigs from sda 3 and 6 gigs from sda 1. These partitions are half the size of sda 2 which is missing 11 or 12 gigs depending on what program you use to view the disk usage.

For a 500 gig drive should I be losing 24 gigs of space?

---

### Post by oldos2er on 2007-12-30
> **cwrann said:**
> The ubuntu OS is not installed on this partition. Can I safely unmount the partition and then FSCK it and then remount it without losing the partitions contents.
Also I think that the warning that appears is a generic warning when running the fsck command. Can anybody verify that this is a generic warning or does it only apply to corrupt file systems.

 You would see this warning if you're about to run fsck on a mounted partition. You should only run fsck on an unmounted one.

---

### Post by elithrar on 2007-12-30
> **cwrann said:**
> 
For a 500 gig drive should I be losing 24 gigs of space?

A 500GB (decimal) drive is 500 billion bytes; which comes down to about ~465GB (binary; actual size). 121GB (sda1) + 217GB (sda2) + 122GB (sda3) = 460GB. It doesn't look like you're missing much of anything at all.

---

### Post by mcduck on 2007-12-30
5% of the disk space on Ext2/3 filesystems is reserved for root user only. This is to prevent situations when user gets the disk so full that the machine runs out of disk space, when root still has 5% of more space he can boot the machine and remove some files..

But if it's not your system partition you can of course disable this 5% limit and set it to 0% instead. Tune2fs is the tool you need (replace /dev/sda2 with the correct partition):
```
sudo tune2fs -m 0 /dev/sda2
```


From 'man tune2fs':
-m reserved-blocks-percentage
              Set  the  percentage  of the filesystem which may only be allocated by privileged processes.   Reserving some number of filesystem
              blocks for use by privileged processes is done to avoid filesystem fragmentation, and to allow system daemons, such as syslogd(8),
              to  continue  to  function  correctly  after non-privileged processes are prevented from writing to the filesystem.  Normally, the
              default percentage of reserved blocks is 5%.

---

### Post by SOULRiDER on 2007-12-30
For starters you could clean your package cache
```
sudo aptitude clean
```

---

