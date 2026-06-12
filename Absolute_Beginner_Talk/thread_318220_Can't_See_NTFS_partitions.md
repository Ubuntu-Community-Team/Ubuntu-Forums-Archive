---
title: "Can't See NTFS partitions"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by buckethead on 2006-12-13
Sorry Everyone, I'm the new newbie in town!

I bet this question gets asked ALL the time.  Anyway i have a number of partitions, one with ubuntu and 2 NTFS with Windows

I want to get access to the NTFD partitions.  i know i have to mount the partition to an temp folder.  however i don't know how.

I'm reading a book and it says to access the disk manager...where is that?
it says to go system -> admin ->disks but its not displayed

another solution says to u gnome partition editor... however i can't locate the mount function. :( 

another solution says to use fdisk -l in the terminal, however when i use this nothing is displayed. :( 

Arghhhh!

Anyway, any help would be great.

---

### Post by Sef on 2006-12-14
> another solution says to u gnome partition editor... however i can't locate the mount function.

[GParted]("http://gparted.sourceforge.net/livecd.php") is a live cd.  Download and burn it, and you should see the partitions.

> another solution says to use fdisk -l in the terminal, however when i use this nothing is displayed.


In the terminal type this:  ```
sudo fdisk -l
```

---

### Post by housam on 2006-12-14
> **buckethead said:**
> Sorry Everyone, I'm the new newbie in town!

I bet this question gets asked ALL the time.  Anyway i have a number of partitions, one with ubuntu and 2 NTFS with Windows

I want to get access to the NTFD partitions.  i know i have to mount the partition to an temp folder.  however i don't know how.

I'm reading a book and it says to access the disk manager...where is that?
it says to go system -> admin ->disks but its not displayed

another solution says to u gnome partition editor... however i can't locate the mount function. :( 

another solution says to use fdisk -l in the terminal, however when i use this nothing is displayed. :( 

Arghhhh!

Anyway, any help would be great.

If you can see them but can't get through, you can read [this]("http://doc.gwos.org/index.php/DapperGuide#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only").

---

### Post by buckethead on 2006-12-15
Hi Thanks for the help

I managed to get the NTFS (windows) partition to auto load onto my desktop.
Thats gr8 and thanks for you help.

Anthony

---

