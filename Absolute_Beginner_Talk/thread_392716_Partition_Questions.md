---
title: "Partition Questions"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by Bungo Pony on 2007-03-24
So, now that Ubuntu is happy, I need to do some hard drive work. Ubuntu is on a 6G hard drive, Win2k is on a 20G partition, and the rest of the drive with win2k is an unformatted partition (140G).

I have a feeling that 6G isn't going to be enough for ubuntu, so I was thinking of making 15G for linux to use, and the rest FAT32 for both systems to use.

Now, I've never done much work with partitioning. In fact, doing up the Win2k partition was probably the extent of my knowledgeable abilities. What would I use to accomplish this?

---

### Post by xXx 0wn3d xXx on 2007-03-24
Well you have a we options. The one I would suggest would be to use GPARTED Live CD. It is very easy to use and you can do almost anything with it. I do not think you can resize XFS/JFS but I haven't been using Ubuntu in a long time.

[Live CD Download](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

### Post by seshomaru samma on 2007-03-24
you can just install gparted
```
sudo aptitude install gparted
```
if i'm not mistaken you dont need to run it from the live CD - it should be just fine running it from ubuntu
format the partition you want to use as ext3 then follow [this guide ]("http://www.psychocats.net/ubuntu/mountlinux")to mount it

---

### Post by machoo02 on 2007-03-24
If you are going to resize your Ubuntu system parition, you will not be able to do that while the partition is mounted, so your best bet would be the GParted live cd or the [System Rescue CD]("http://www.sysresccd.org/").

You could also consider partitioning your remaining space as ext3, and installing the [Windows Ext2/3 driver]("http://www.fs-driver.org") in order to mount it from Windows.

---

