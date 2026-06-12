---
title: "Windows NTFS partition disappered during installation"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by ggatti on 2008-03-04
HELP!

I have installed UBUNTU 7.10 today on a HP Pavillon computer (this is the third computer I tried Ubuntu. In the first two everything went well and they have dual boot with WIndows XP and Ubuntu, the third time it went terribly wrong....).

During the installation I have used the automatic partition expecting, as it happend on the first two computer, that the installation would keep Windows XP NTFS partition.

Instead, at the end of the installation at boot up I do not get the alternative to choose Windows XP, and in Ubuntu if I type df I do not get any wondows partition metinoned.

I have lots of data without, unfortunately, backup on the NTFS partition, including pictures of my children when they were babies.

Is there a way to recover all or at least a par tof the data?

Thanks a lot! I am disperate!

---

### Post by glennric on 2008-03-04
Post the output of 
```
sudo fdisk -l
```
and perhaps the output of
```
cat /etc/fstab
```
as well.

---

