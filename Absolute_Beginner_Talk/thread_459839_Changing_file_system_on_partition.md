---
title: "Changing file system on partition"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by Bheeit on 2007-05-31
Hi,

I am a new Linux user and have Installed Ubuntu on a deticated PC that I have to have act as a basic file server and email server, at the moment I have Samba working on the network and most things working after much research and practise, But I am having trouble reformatting two FAT32 partitions back to ext3, they mount automatically and I have tried the umount command and keep getting errors, If someone could help me this would be great. If I had have known that linux did not support permisions in FAT32 i would have formatted them all in ext3 as Samba reads them fine from my windows machines.


thanks

Byron

---

### Post by plcdfa on 2007-05-31
FAT32 doesn't support file permissions at all, no matter from what OS you're using it. What error message do you get when trying to umount the partitions?

---

### Post by LaRoza on 2007-05-31
If you want to reformat a partition or hard disk, I would recommend using GParted LiveCD

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Being a live cd, it is very easy to work with, and is very graphical.

---

### Post by plcdfa on 2007-05-31
> **LaRoza said:**
> If you want to reformat a partition or hard disk, I would recommend using GParted LiveCD

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Being a live cd, it is very easy to work with, and is very graphical.

That really is a great tool, "saved my life" some days ago. Too bad my mouse always freezes in it. :(

---

### Post by LaRoza on 2007-05-31
Your mouses freezes? Maybe using a newer version, if there is one, than the one you have will work.

Using a different mouse might work also.

GParted is one the most useful tools I have seen.

---

### Post by plcdfa on 2007-05-31
I used the newest version (downloaded it one week ago). My mouse is a USB mouse made by "Hama" Not the biggest brand :), german I think. But really don't wanna go off topic. I got along with keyboard well anyway.

---

