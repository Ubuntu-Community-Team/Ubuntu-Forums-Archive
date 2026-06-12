---
title: "Install alternative iso"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by jhawk43 on 2007-06-29
Here is what I would like to do, not sure if it is possible, please help is possible.

1. Create a partition on my internal hard drive using Acronis Disk Director.

2. Install ubuntu alternative iso into that partition

3. Use Acronis OS selector to boot.

This would mean I think not installing grub, which I don't want to do.

Any help would be appreciated. Thanks

---

### Post by davidjmayo on 2007-06-29
delete

---

### Post by steve.horsley on 2007-06-29
This is not easy. 

Firstly, you need 2 partitions for Ubuntu, not 1. The easiest way is to leave unpartitioned space and tell the Ubuntu installer to use the free disk space - the installer will create two partitions as needed, and format them appropriately (one with ext3 and one as a swap partition).

It is possible (using the alternate installer and manual partitioning) to tell the installer to install GRUB on the Ubuntu system partition instead of the disk MBR. This would allow you to continue using Acronis, I guess. Unfortunately, the installer has a fatal bug and fails to install all the required configuration files if yoiu choose this option. You have to create and manually edit the required files by hand, using a live CD.

Overall., you best bet is to allow the installer to overwrite the MBR, then from the running Ubuntu, install GRUB to the Ubuntu system opartition, then replace the MBR with Acronis from a backup.

---

