---
title: "Partitions for dual boot?"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by ubername on 2007-02-03
Hi

This is a follow up topic from 'I cannot get my live CD to run Ubuntu' I have downloaded 6.06 and burnt it to disk and am happy to say it will boot to ubuntu (unlike the 6.10 disk I have been trying)

However, after going through the various location and user identification options I get to the partitioning bit.

The install agent tells me I have (things I previously sorted out mostly)

/dev/hda1 Fat16 47Mb
/dev/hda4 Ext3 6.83 Gb
/dev/hda3 Fat32 2.93 Gb
/dev/hda2 NTFS 64.7Gb

I am trying to put ubuntu ("/" as I understand it) onto hda4, with the swap file on hda3.

When I try and do this I get (after a while) "the test of file system with type FAT16 in partition #1 of IDE1 master (hda) found uncorrected errors"

Any clues? I don't know whether I need this (fat16) partition or not, I certainly didn't set it up myself!

---

### Post by rccharles on 2007-02-03
> **ubername said:**
> Hi

This is a follow up topic from 'I cannot get my live CD to run Ubuntu' I have downloaded 6.06 and burnt it to disk and am happy to say it will boot to ubuntu (unlike the 6.10 disk I have been trying)

However, after going through the various location and user identification options I get to the partitioning bit.

The install agent tells me I have (things I previously sorted out mostly)

/dev/hda1 Fat16 47Mb
/dev/hda4 Ext3 6.83 Gb
/dev/hda3 Fat32 2.93 Gb
/dev/hda2 NTFS 64.7Gb

I am trying to put ubuntu ("/" as I understand it) onto hda4, with the swap file on hda3.

When I try and do this I get (after a while) "the test of file system with type FAT16 in partition #1 of IDE1 master (hda) found uncorrected errors"

Any clues? I don't know whether I need this (fat16) partition or not, I certainly didn't set it up myself!

I think the fat16 partition could be some type of Windows control partition.  

If you are sure you do not have anything on hda3, you need to repartition this partition to type swap.

Robert

---

### Post by bodhi.zazen on 2007-02-03
I would ignore that error message ....

I would also delete both hda3 and hda4

Make a new partition for root and swap, format both.
[indent]/ = ext3 swap needs to be formatted as swap ...[/indent]

Size of swap = RAM X 2, max 1 Gb

Rest give to / (root)

Install GRUB to MBR

You should then be good to go ;)

---

### Post by ieee488 on 2007-02-03
Agree with rccharles that the FAT16 is some sort of Windows recovery partition. 
My newer Dell had something like that.

Agree about deleting the deleting /dev/hda3 and /dev/hda4 leaving you with /dev/hda2 which is NTFS.

Resize NTFS partition smaller. Create a new swap partition and a new partition for /.

---

### Post by ubername on 2007-02-03
YEEHAA!

Posting from an ubuntu booted machine from the hard drive!

Thanks to everyoone. I can't remember exactly whose advice got me thorugh but it was a team effort so thanks a mill!

Now wait for the flood of calls for help as I actually get using the thing!

Cheers

JP

---

### Post by Tiburon41 on 2007-02-03
> **ieee488 said:**
> Agree with rccharles that the FAT16 is some sort of Windows recovery partition. 
**My newer Dell had something like that.**

Agree about deleting the deleting /dev/hda3 and /dev/hda4 leaving you with /dev/hda2 which is NTFS.

Resize NTFS partition smaller. Create a new swap partition and a new partition for /.


Exactly.  I think it's either a recovery partition or system tools thing that your system vendor put on there when building your system.

---

### Post by ubername on 2007-02-04
> **Tiburon41 said:**
> Exactly.  I think it's either a recovery partition or system tools thing that your system vendor put on there when building your system.

Thanks

Running well at the moment.

I intend to leave the NTFS partition as it is. My family also use this PC  so I need to leave the windows bit alone as much as poss (they'll learn, but one of them is only 6: forcing a new OS on him seems a bit tough!)

In fact, although I appreciate that 3 GB swap for 512Mb Ram is OTT, I will leave it well alone. I am just happy I am up and running!

---

