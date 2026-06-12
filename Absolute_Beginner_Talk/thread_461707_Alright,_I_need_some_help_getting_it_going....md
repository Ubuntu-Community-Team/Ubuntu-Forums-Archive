---
title: "Alright, I need some help getting it going..."
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by ejw2076 on 2007-06-02
Here is where I am...

I have made a computer as a dedicated Linux box.  I would like to run Kubuntu 7.04 on it but there is one thing standing in my way - I have a raid 0 array I need to set up.   Basically I don't know how to "mount" the array. It is two 37 gig WD Raptors as a 72 gig drive on my bios raid (abit Fatal1ty), and I can't figure out how to partition it as one hard drive.  I want it viewed as one hard drive as I view it in fdisk, that way I can have the swap drive span across both hard drives to increase efficiency.  I have a feeling that the answer I am looking for is very simple, as I haven't been able to find it anywhere.  Basically, how do I mount the disk before doing anything to it?

---

### Post by jakev383 on 2007-06-02
One more before I go to bed....
If you know where it's mounting, then you can see the partitions by doing:
sudo fdisk -l /dev/sdc
or whatever the drive is. Then create a folder somewhere, and mount it:
sudo mount /dev/sdc1 /testfolder
It should mount if it knows what the filesystem is.
As far as the RAID, if it's done on a BIOS level it should either show as 1 drive anyway. If not try gparted and see what it's showing up as.

---

