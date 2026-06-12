---
title: "Extra FAT32 Partition?"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by wnt22 on 2007-05-11
I just installed Ubuntu a couple of days ago on to my external hard drive.  When I was installing I did the guided install so Ubuntu set up my partitions.   Now I want to make an extra partition into FAT32 so that I can still store some stuff on to my External Hard Drive from Windows.  My external hard drive is 200G so I have plenty of room.  Right now my external hard drive breaks down like this... 

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       23944   192330148+  83  Linux
/dev/sdc2           23945       24321     3028252+   5  Extended
/dev/sdc5           23945       24321     3028221   82  Linux swap / Solaris



My question is how could I shrink the sdc1 or split it in two or something to make an extra partition so I could make that one FAT32?

thanks.

---

### Post by Foxmike on 2007-05-11
Try out installing gparted if you are undger GNOME (Ubuntu) or qtparted if you are under KDE (Kubuntu).

```
sudo aptitude install gparted
```

This is the partition manager.  With this you can select the drive/partition you want to work and you can resize/delete it.

As well, you would be pleased to know that there is a Windows driver that allows you to read/write ext2fs/ext3fs drives as if they where FAT32.  Here is the link:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

Of course if the partition is ext3 (journalising) then it will not follow the journal of the file system tho.

Good luck!:)

Regards,

-FM

---

### Post by wnt22 on 2007-05-11
I have gparted, but it's not letting me edit my external hard drive files.  It's showing they are locked or something? The only option available for them is to be unmounted and it won't let me do that.  Do I need to go through the LiveCD to change them or is there a (safe) Windows program I could do it from?

---

