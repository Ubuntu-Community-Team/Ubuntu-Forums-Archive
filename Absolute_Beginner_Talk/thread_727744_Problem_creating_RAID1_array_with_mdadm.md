---
title: "Problem creating RAID1 array with mdadm"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by mgbridges on 2008-03-18
I have two 200GB drives which were previously part of a hardware RAID1 setup on my old Windows machine. I want to make them a RAID1 pair on my Ubuntu machine. They are detected fine by Ubuntu as /dev/sdb1 and /dev/sdc1. They were each formatted as a single ntfs partition.

After doing some research on this forum I found mdadm and installed it. I read the README.recipes file and decided to follow step 10 - Convert existing filesystem to RAID1. However, I din't bother with copying the data from one disk to the other as I had already backed up the contents to a separate disk.

I followed the steps as follows:
```
    mdadm --create /dev/md0 -l1 -n2 /dev/sdc1 missing
    mkfs -t ext3 /dev/md0
    mount /dev/md0 /media/DOCS_2
    mdadm --add /dev/md0 /dev/sdb1

```

All went well up to the last stage, at which point I got the error:
```
mdadm: /dev/sdb1 not large enough to join array
```

Any ideas?

Martin

---

### Post by Paul Weaver on 2008-03-18
Obvious question, but are sdb1 and sdc1 the exact same size? 

Try
mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/hdb1 /dev/hdc1

(Assuming both drives are emptiable)

cat /proc/partitions will show you the number of blocks

---

### Post by mgbridges on 2008-03-18
Yes, both disks are 200GB disks. Both are the same model of Seagate too so there shouldn't be any difference in size.

Martin

---

### Post by toupeiro on 2008-03-25
Hi Martin,

Out of curiosity, have you made sure your system does not support Hardware raid?  HW Raid is so much better and faster.  You have a dedicated RAID controller to help with the data I/O, You get the automatic rebuild of your new devices, plus all that load off your CPU.

Its usually access through your system BIOS.

---

### Post by mgbridges on 2008-03-25
I'm not 100% certain whether there is on-board support for hardware RAID or not. However, I've read various articles which argued both in favour and against hardware RAID. The CPU is fairly lightly loaded so I went for software.

Still willing to be persuaded otherwise tho!

Martin

---

