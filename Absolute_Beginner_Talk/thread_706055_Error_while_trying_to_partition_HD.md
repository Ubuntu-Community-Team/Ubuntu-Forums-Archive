---
title: "Error while trying to partition HD"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by UFRaymond on 2008-02-24
I just got the, "Beginning Ubuntu Linux," second edition book and am on Firefox via Ubuntu.  So far I've only run into one error while trying to partition my hard drive.  I'm doing this manually, and I've read many a time through manually partition the HD in my handy dandy little book, and nothing has talked about this error even in the installation errors.

"**An error occured while applying the operations**

The following operation could not be applied to disk:

Resize /dev/sda2 from 74.47 GiB to 51.98 GiB

See the details for more information"

And after looking at the details, my error occured while Gparted was trying to resize my main partition which Windows runs on.  I have re-tried partition a few times, and I can confirm there is a decent amount of white block after my main partition [holding windows].

What to do... :mad:

---

### Post by oedha on 2008-02-24
have you defrag your windows partition before resize it ? (many people said...twice)
and you can also resize the partition from ubuntu live cd too......

---

### Post by InfinityCircuit on 2008-02-24
Well, first of all make sure that Windows still boots and that you haven't screwed it up too much.  I'd also recommend defragmenting the Windows drive prior to repartitioning.

Ubuntu does not ship with the newest version of NTFS partitioning software.  Parted Magic 2.0 was just released, you can download the live CD and it should have the highest probability of successfully formatting your harddisk.

---

### Post by housam on 2008-02-24
> **UFRaymond said:**
> I just got the, "Beginning Ubuntu Linux," second edition book and am on Firefox via Ubuntu.  So far I've only run into one error while trying to partition my hard drive.  I'm doing this manually, and I've read many a time through manually partition the HD in my handy dandy little book, and nothing has talked about this error even in the installation errors.

"**An error occured while applying the operations**

The following operation could not be applied to disk:

Resize /dev/sda2 from 74.47 GiB to 51.98 GiB

See the details for more information"

And after looking at the details, my error occured while Gparted was trying to resize my main partition which Windows runs on.  I have re-tried partition a few times, and I can confirm there is a decent amount of white block after my main partition [holding windows].

What to do... :mad:

- First of all you have to back-up your data - just in case.
- Do defrage your HDD 2-3 times and notice the position of the green sector ( windows file system ) . let say at 40% from the left side.
- This means that you cann't resize windows partition to less than that size of the HDD or you'll damage it.
- Use Gparted tool ( on the live CD ) to do the partitioning task.
- You can create up to only 4 primary partitions on single HDD.
-I suggest to create 3 primary partitions and make the 4th one as extended which can be devided to many logical partitions.
- You'll devide the extended partition to 2 partitions : one EXT3 ( 20 GB is a good space ) for installing ubuntu as a root partition ( / ). and the other one as a swap ( only 1 GB ).
- During the installation process when it comes to the partitioning choice choose the manual way and assign the EXT3 as a root ( / ) .

GOOD LUCK

---

