---
title: "Partition help please. I'm lost."
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by Arazu on 2008-04-17
I'm trying to set up the partitions and am having trouble. I set up a partition for Ubuntu when I installed Vista so my partitions look like this in GParted:

/dev/sda1 fat 16 39.19 MiB
/dev/sda2 ntfs 175.78GiB (Vista's partition)
/dev/sda3 unknown 122.27GiB

Obviously I want to install into /dev/sda3 but I can't create any more partitions for swap and  if I don't chose manual the installer wants to use the entire drive. I also can't do anything to sda3 because it's unformatted space.

How should I proceed?

---

### Post by dstew on 2008-04-17
Use gparted again, delete the 122 gb partition, and create a 121 partition for your root file system, and a 1 gb partition to use as swap. Don't bother formatting them, do that during the installation. Use Manual mode during the installation. During the installer, you will need to check the format box for the large partition, format it as ext3, give it the mount point / (called "root"). For the smaller partition, tell it to use as swap, no need to format it or give it a mount point.

---

### Post by wolfen69 on 2008-04-17
you need to resize sda3. choose manual and resize to 121gb. that will leave over a gig for swap. the mount point for sda3 will be /

make sda3 ext3 and swap will be made "swap".

you also may want to read this: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Arazu on 2008-04-17
Thanks much!!!

---

