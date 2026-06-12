---
title: "[SOLVED] fstab new partition"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by alphaniner on 2007-12-17
I'm trying to auto-mount a newly minted partition with fstab.  Here is the output of fdisk -l:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10831082

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1307    10498446    7  HPFS/NTFS
/dev/sda2            1308        1320      104422+  83  Linux
/dev/sda3            1321        1942     4996215   83  Linux
/dev/sda4            1943       30401   228596917+   5  Extended
/dev/sda5            1943        2191     2000061   82  Linux swap / Solaris
/dev/sda6            2192       30401   226596793+  83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3ae5ba96

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7833    62918541    7  HPFS/NTFS
/dev/sdb2            7834       38913   249650100   83  Linux

```

/dev/sdb2 is the new partition, made using fdisk and mkfs.  Anyhoo, after I reached this point I went into /dev/disk/by-uuid and got the UUID for the new partition.  I then added the following line into fstab:

```
UUID=...............     /bucket     ext3     defaults     0     2 
```

I rebooted, and I got an error something to the effect that the UUID was not found, and I got stopped at the command line.  I had made a backup copy of my old fstab so I just restored that and rebooted.  Ubuntu loaded and I had a new "238.2G Volume" or something in my file manager.  I was able to open it, the only wierd thing was that, although it was called "238.2G Volume" it only showed about 222G of free space.

At any rate, I had backed up the new (broken) fstab so I checked that out and I found that the UUID I had used for the new partition no longer existed in /dev/disk/by-uuid, there was a completely different UUID for the partition.  I had copied and pasted it into fstab so I know it wasn't a typo or anything.  And besides, when I say completely different I mean completely different.  There wasn't even the slightest resemblance between the two.  Well, i tried replacing the UUID in fstab with /dev/sdb2, ie:

```
/dev/sdb2     /bucket     ext3     defaults     0     2 
```

and rebooting.  This time I have booted, but the drive is not showing up as /bucket, nor as "238.2G Volume."  That is to say, it is not showing up at all. Just for poops and giggles I'm going to try the *new* :???: UUID real quick, but if anyone has any insight to offer it would be greatly appreciated.

a9

---

### Post by santaslittlehelper on 2007-12-17
This might be helpful.
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Also you could post you're fstab.

---

### Post by logos34 on 2007-12-18
> **alphaniner said:**
> This time I have booted, but the drive is not showing up as /bucket, nor as "238.2G Volume."  That is to say, it is not showing up at all. Just for poops and giggles I'm going to try the *new* :???: UUID real quick, but if anyone has any insight to offer it would be greatly appreciated.

Maybe you forgot to create the mountpoint?

sudo mkdir /bucket

(actually it would probably be better to put it inside /media--that's the customary place).

I think it reserves some space for lost&found, and some is taken up in the formatting.  I think the default is 5% of disk space reserved (root) when you install.  But 16 gb diff seems odd. 

I have problems with uuids too--especially blkid, which seems not to report the new uuid of a formatted partition until after a reboot or even later.  /dev/disk/by-uuid is a lot better but not perfect.

---

### Post by alphaniner on 2007-12-18
> **logos34 said:**
> Maybe you forgot to create the mountpoint?

sudo mkdir /bucket

Yuppers.  I just realized the mountpoint thing a few minutes ago.  That did the trick.

> **logos34 said:**
> (actually it would probably be better to put it inside /media--that's the customary place).

Part of me really wants it to show up right in the File System like my windows partitions :twisted:.   The whole partition as a folder thing still seems a bit odd.

> **logos34 said:**
> I think it reserves some space for lost&found, and some is taken up in the formatting.  I think the default is 5% of disk space reserved (root) when you install.  But 16 gb diff seems odd.

I saw the 5% for Super User bit when I partitioned with mkfs, but didn't know what to make of it at the time.  That would be ~12GB, leaving ~4 unaccounted for.  If I could figure out what's going on in the Disk Usage Analyzer maybe that would shed some light on things.  That's probably the most confusing aspect of Ubuntu I've come across so far :shock:

> **logos34 said:**
> I have problems with uuids too--especially blkid, which seems not to report the new uuid of a formatted partition until after a reboot or even later.  /dev/disk/by-uuid is a lot better but not perfect.

I don't know what blkid is, but in my case a UUID was reported, it just changed after the first reboot after creating the partition.  I got the UUID I used from /dev/disk/by-uuid, so I have no idea why it changed.

Anyway, thanks a bunch for all the help and info!

a9

---

