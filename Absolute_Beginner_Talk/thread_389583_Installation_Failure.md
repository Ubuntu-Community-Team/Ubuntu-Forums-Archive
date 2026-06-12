---
title: "Installation Failure"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by DRoll221 on 2007-03-20
Hello everyone,

I'm new to Ubuntu, i've been visiting the forums for the past few weeks, and finally decided to install 6.10 on an old computer of mine.  I was planning on reformatting the entire hard drive just to dedicate to Ubuntu, as it has XP on it and I really don't use the computer anymore.  I boot fine off of the CD, try to install and choose the "erase entire disk" option and go through the steps and it gives me the error "The creation of swap space in partition #5 of IDE1 master (hda) failed."...I've searched online and haven't found an answer.  Can anybody help? Thank you

---

### Post by rusty4r on 2007-03-20
Go back to that step and try to do it manually, ie..choose the manually edit partitions. and delete all partitions then create one partition that uses up the entire drive except for about 1gig and then create a partition of that last gig. On the next step you will mount the large partition as / and the small one as swap.

This guide was a lot of help to me
[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")

---

### Post by freebeer on 2007-03-20
I'm wondering if that section of the hard drive has bad sectors?

You could try manually setting up your partitions, and maybe leaving that section out of the partition set?

---

### Post by DRoll221 on 2007-03-21
thanks for the responses guys...So I've tried to manually edit the partition table and it says that the entire hard drive is unallocated, even though i have XP on it and a lot of files...and I try and create a new partition, and set the disk label to msdos and it says "Error while setting new disklabel"

---

### Post by cowlip on 2007-03-21
MAybe try the alternate install iso or use the command line tool "fstab"?  It sounds like there could be a problem with gparted (not the most bug-free program).

---

