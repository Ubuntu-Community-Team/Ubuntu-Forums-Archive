---
title: "Re-partitioning harddrive - from NTFS to EXT3"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by cyhk on 2008-02-23
Hello.

I have three HDD's, one of which has all NTFS partitions.  I am attempting to replace them with one ext3 partition.  I've tried Gparted, it shows a lock by the hdb2 drive, and won't let me delete any of them.  

Gparted shows:
/dev/hdb2 - lock
- /dev/hdb5 - triangle w/ exclamation point
- /dev/hdb6 - triangle w/ exclamation point
- /dev/hdb7 - triangle w/ exclamation point
- /dev/hdb8 - triangle w/ exclamation point & lock

Any clue?

Also, does it usually take 5 min or so for Gparted to scan all the drives? I'm hoping its just my hdb hdd causing the slow action, though I'm not sure.

Cheers.

---

### Post by taurus on 2008-02-23
Is the drive currently mounted?  You cannot delete or format mounted drive so you need to unmount it first.  Otherwise, do it from the LiveCD if you have the LiveCD handy.

```
df -h
```

---

### Post by asmoore82 on 2008-02-23
> **cyhk said:**
> 
Also, does it usually take 5 min or so for Gparted to scan all the drives?
I'm hoping its just my hdb hdd causing the slow action, though I'm not sure.

If you run GParted from a terminal, you can see what's taking so long;
In my experience, it is always a phantom floppy drive.

You can speed things up a lot by telling GParted which drive to manipulate on the command line;
but of course, this is only useful when you know which drive ahead of time, example:
```
sudo gparted /dev/hdb
```

you may be able to get a quick clue as to which device the drive you want is with this:
```
sudo fdisk -l
```(lowercase 'L')

---

### Post by cyhk on 2008-03-08
Thanks for the assistance!

I've got the drive formatted now, although I can't write to the drive.  In GParted its locked.  How do I unlock it so I can access it?

Thanks!

cyhk

---

### Post by taurus on 2008-03-08
Have you mounted them and where do you mount them to?

Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
df -h
id
```

---

### Post by cyhk on 2008-03-08
Here's the output for the commands you mentioned.  Not sure as to what you mean by where I mounted them to.

**cyhk@Perception:~$ sudo fdisk -l**
[sudo] password for cyhk:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbbf6bbf6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       30050   210660345   83  Linux
/dev/sda3           30051       30401     2819407+   f  W95 Ext'd (LBA)
/dev/sda5           30051       30401     2819376   82  Linux swap / Solaris

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       24792   199141708+  83  Linux


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS


**cyhk@Perception:~$ cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=70548468-5d14-4079-a739-a38fbfd936b7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d617268c-5806-4263-8c37-fafcbd0a7453 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

**cyhk@Perception:~$ df -h**
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             198G   24G  164G  13% /
varrun                470M  128K  470M   1% /var/run
varlock               470M     0  470M   0% /var/lock
udev                  470M  156K  470M   1% /dev
devshm                470M     0  470M   0% /dev/shm
lrm                   470M   39M  432M   9% /lib/modules/2.6.20-16-generic/volatile
/dev/hdd              143M  143M     0 100% /media/cdrom1
/dev/sdb1             466G  386G   81G  83% /media/FourSquare
/dev/hdb1             187G  188M  178G   1% /media/disk

**cyhk@Perception:~$ id**
uid=1000(cyhk) gid=1000(cyhk) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin),1000(cyhk)

---

### Post by taurus on 2008-03-08
I assume you are talking about /dev/hdb1 mounted to /media/disk.

Try

```
sudo chown -R cyhk:cyhk /media/disk
ls -la /media
```
You should be able to write to /media/disk anytime you want without using sudo/gksudo now.

---

