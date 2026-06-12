---
title: "Question about External Hard Disks"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Wake Rider on 2007-04-18
I have an external hard disk (300 GB). For some reason when it is plugged into Ubuntu, it will let me read it but not write. It uses the NTFS file format system, I once tried to change it to FAT32 but it wouldn't let me. How do I get Ubuntu to read AND write to an NTFS formatted drive?

---

### Post by heimo on 2007-04-18
See if this helps:
[https://help.ubuntu.com/community/VolumePermissions](https://help.ubuntu.com/community/VolumePermissions)

---

### Post by trishacupra on 2007-04-18
> **Wake Rider said:**
> I once tried to change it to FAT32 but it wouldn't let me.

Please elaborate on that.

---

### Post by Yes_It's_Me on 2007-04-18
Linux does not support ntfs writing by default, follow that link above.

then afterwards do a search on the forum for ntfs write, you will find instructions on installing ntfs writing

---

### Post by Wake Rider on 2007-04-22
> **trishacupra said:**
> Please elaborate on that.

In Windows Explorer (On my Windows computer, I am not running a dual-boot system, Linux and Windows have their own computer) I right-clicked on the drive and clicked format in the options. I looked under drive type but it only had NTFS.

---

### Post by Wake Rider on 2007-04-22
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#head-62bb8324b93c2b77797bbd3e45493f08ad90a52c](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#head-62bb8324b93c2b77797bbd3e45493f08ad90a52c)

I am on 7.04. I followed the instructions in the above link, I have enabled write support in the configuration, but when I try to write anything to my external hard disk it still tells me I don't have permission to access it. How do I change this?? 

Also, how do I go into directories using the cd command into an external device? I only know how to use the cd command on everything contained within the home folder on the internal hard disk.

---

