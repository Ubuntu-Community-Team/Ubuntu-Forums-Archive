---
title: "Kubuntu doesn't show mounted partitions anymore."
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by keith11 on 2007-05-14
I am facing a seemingly strange problem. I was working in windows and suddenly I got the feared blue screen of death and the system crashed. I have a dual boot with Kubuntu 7.04 and after the system restarted, I booted into Kubuntu to discover that the /media/sda1 and /media/sda5 don't display any files in those windows partitions. Both of those partitions are NTFS. I can still see files in one partition /media/sda6 which is a fat32. It is strange because I can see how much the partition are full but I just can't see the files. I did take a look to my /etc/fstab and it seems fine. I looked at the properties of the partitions(the "meta data" tab of properties) which don't show the files and they don't seem to be mounted. Any ideas how I can fix this problem? Thanks.

Keith.

---

### Post by Happy_Man on 2007-05-14
```
sudo mount /dev/sda1 /media/sda1
sudo mount /dev/sda5 /media/sda5
```
see if that works...

---

### Post by keith11 on 2007-05-15
> **Happy_Man said:**
> ```
sudo mount /dev/sda1 /media/sda1
sudo mount /dev/sda5 /media/sda5
```
see if that works...

I already did that and that didn't work. I don't know what was wrong but the error doesn't appear anymore. Thanks for your suggestions.

Keith.

---

