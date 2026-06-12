---
title: "persistence and drive size..."
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by stevenrushing on 2007-05-16
I am following the directions at :[https://help.ubuntu.com/community/LiveCDPersistence](https://help.ubuntu.com/community/LiveCDPersistence)


They are quite straight forward and easy all the way up until here:

> $ dd if=/dev/zero of=/media/hda1/casper-rw bs=1M count=128
128+0 records in
128+0 records out
134217728 bytes transferred in 0.947819 seconds (141606919 bytes/sec)

$ mkfs.ext3 /media/hda1/casper-rw
mke2fs 1.38 (30-Jun-2005)
/media/hda1/casper-rw is not a block special device.
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=1024 (log=0)
Fragment size=1024 (log=0)
32768 inodes, 131072 blocks
6553 blocks (5.00%) reserved for the super user
First data block=1
16 block groups
8192 blocks per group, 8192 fragments per group
2048 inodes per group
Superblock backups stored on blocks:
        8193, 24577, 40961, 57345, 73729

Writing inode tables: done
Creating journal (4096 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 23 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.


I have a 10G portable hd.  Are these commands different for different sized drives?  I can only imagine that they would be.  how do I know what to type differently?

Thank you for any assistance!  =)

---

### Post by FuturePast on 2007-05-16
And how exactly do you want to use the external HD?

You are confusing two methods: 
One way is to create a file on the internal HD, using the dd command.
The other is to create a whole partition on an external device with a filesystem (mkfs) labelled casper-rw.

Which do you want to use?

---

### Post by stevenrushing on 2007-05-17
Thank you.  Yes, i wasn't reading closely enough.  I was trying to do both when I only needed to do one.  =)

---

