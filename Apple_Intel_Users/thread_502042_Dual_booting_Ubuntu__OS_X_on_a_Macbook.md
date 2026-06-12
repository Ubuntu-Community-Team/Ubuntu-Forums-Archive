---
title: "Dual booting Ubuntu / OS X on a Macbook"
date: 2007-07-16
forum: Apple Intel Users
---

### Post by Kethinov on 2007-07-16
Steps I've taken:

1. Install OS X
2. Run boot camp and create a partition for "Windows"
3. Boot Ubuntu LiveCD
4. At partitioning, I switch to manual
5. At manual partitioning, I select sda3 (the "Windows" partition) as /
6. Proceed with install, everything goes fine
7. Reboot to unbootable Linux system

Tried again following the steps here: [http://bin-false.org/?p=17](http://bin-false.org/?p=17)

No luck.

---

### Post by anujseth on 2007-07-16
[http://ubuntuforums.org/showthread.php?t=452262](http://ubuntuforums.org/showthread.php?t=452262)

---

### Post by Kethinov on 2007-07-16
What is the difference between that guide and the steps I've taken?

I've essentially done exactly that and I always end up with an unbootable system.

---

### Post by cyberdork33 on 2007-07-16
did you format it?

---

### Post by Happy Dave on 2007-07-17
Hey, I just did the same thing.

The key here is not to simply select the sda 3 partition - that's been setup for windows.

Instead, delete that partition, and create one partition on '/' and a swap partition of 512mb.  Proceed from there and it should work.

---

### Post by Happy Dave on 2007-07-17
Here's the relevant part from the tutorial you linked to:

> 
Restart and boot into the Live CD by pressing the Option key at startup. Ubuntu boots. Click the Install icon on the desktop. Follow simple instructions until you come to the Partitioning screen(Step 4). Select 'Manual' partitioning here. Check the box in front of the Linux partition you created (54GB) /dev/sda3 in my case. This is why I earlier said the size of the Linux partition is not important. When you delete this partition it gets merged with the free space which is what we will use to install Ubuntu. You need to create 2 partitions one to mount root '/' i.e. your linux file system and a swap space. Select the free space and create a 'New Partition'. Select this such that 1GB remains for the swap space (or less or more as you see fit, swap can be resized later). Select this partition (53 GB for me) to be 'ext3' formatted and give it a '/' mount point. Create another partition from the remaining free space and use it as swap. The pictures below demonstrate the process.

---

