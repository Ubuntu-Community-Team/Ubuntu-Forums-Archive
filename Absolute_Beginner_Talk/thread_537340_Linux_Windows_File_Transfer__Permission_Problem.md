---
title: "Linux Windows File Transfer / Permission Problem"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by Andrew Garn on 2007-08-28
I have two physical disks:

2x 320gb SATA's

The first has:

- a 280gb NTFS Windows Partition with vista installed on it
- a 38gb main ubuntu partition
- a 2gp ish ubuntu swap file partition

The second has:

a 320gb NTFS partition - it is empty.

-----------------------------------------

When I have ubuntu loaded It shows me two mounted partitions disk and disk1, I want to be able to copy/edit files on those disks but i cant work out how to be able to set the partitions in a way that allows this.

Help would be appreciated
Thanks

---

### Post by sumguy231 on 2007-08-28
Ubuntu doesn't come with the ability to write to NTFS, so you'll need to install the ntfs-3g driver to write to those partitions. Here's the wiki page on doing that:
[https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite)

---

