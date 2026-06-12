---
title: "install issues"
date: 2006-06-16
forum: Apple PPC Users
---

### Post by James_M on 2006-06-16
I'm trying to install Xubuntu on a PowerBook G4 (12 inch) and I'm having trouble with the install.  I used OS X's Disk Utility to create a partition, but I'm confused as to how to install to it.  I can see it in the installer for Xubuntu, but I'm not sure if It's suppoed to be HFS or ext2/3.  The partition is /dev/hda5.  what am i doing wrong?

---

### Post by aysiu on 2006-06-16
The Xubuntu installer should allow you to reformat the HFS partition to be Ext3.

I don't think OS X's Disk Utility will make an Ext3 partition for you.

---

### Post by tidris on 2006-06-16
What I did was to create free space in the disk using the OSX DiskUtility, then let the ubuntu installer create all the partitions it needs automatically using the free space in the disk. If you let the installer do its thing it creates 3 partitions: a newworld bootstrap one that contains the yaboot bootloader, a root partition in ext3 format, and a swap partition.

The OSX DiskUtility allows you to mark an existing partition as free space. So, if initially you only have one big partition in the disk, to create free space you would create a second partition, then mark one of the two partitions you now have as free space.

You can also create free space with the ubuntu installer by deleting existing partitions, but I feel that can be more error prone when done by people who are brand new to ubuntu/linux.

Yet another way to create free space is to use a linux program called parted to actually shrink an existing hfs or hfsplus partition without erasing it. I feel that is even riskier than the options above and I haven't tried it myself.

---

### Post by James_M on 2006-06-16
It's funny, i did that thing with the free space before i left my house on the longshot that it might actually work, and it did.  I just got back and i see you've posted that.  Thanks for responding so fast, though

---

