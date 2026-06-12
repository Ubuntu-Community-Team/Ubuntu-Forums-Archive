---
title: "Why sd5 i s /SWAP Solaris?"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by dtzxdtzx on 2007-05-14
Hi,

After installing the kubuntu, I typed sudo fdisk -l and got something like:

hda1
hda3
hda5 SWAP /Solaris

I understand all the infor but why the swap partisition is solaris? 

Thanks

Frank

---

### Post by 5-HT on 2007-05-14
The partition system indicators for Linux swap and Solaris partitions happen to be the same 
Fdisk is reporting that your /dev/hda5 partition has an ID of 82, which most often happens to be either a Linux Swap or Solaris partition. Nothing to worry about.

---

