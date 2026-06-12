---
title: "Need to format a Partiton to HFS+"
date: 2008-01-25
forum: Apple PPC Users
---

### Post by benjgvps on 2008-01-25
I need to take a vFat partiton I made in xubuntu, format it to HFS+ (Or HFS, it does not matter) and make it be able to be read by Mac OS 9. I have a bootable copy of the Mac hard drive on a SD card so I could drag and drop the the system folder and applications folder onto a Mac Partition. I can pick the bootable partion if I hold Alt (Option on a Mac keyboard), so I don't have to worry about problems related to that.

---

### Post by frog_pilot on 2008-01-26
There is no way to create a hfs+ filesystem under ubuntu. With gparted you could create a hfs partition which is limited to afaik 2 GB. To create a ususal hfs+ filesystem you need a bootable MacOS Medium. But be aware, reformatting a drive with Diskutility deletes all existing partitions on the drive.

You could reformat only the vfat partition with diskutility without deleting the whole drive - I did it one time. But you need a bootable MacOS Medium (OSX CDROM or similar) to do so.

---

### Post by benjgvps on 2008-01-26
I formatted the hard drive with Drive Setup in Mac OS 9 and made a 4.4 GB partition with about 3.14 GB of free space left over. As I type this I am reinstalling xubuntu taking over all the free space. The only thing I HATE HATE HATE about installing Linux is: Partitioning. Nightmare.

---

