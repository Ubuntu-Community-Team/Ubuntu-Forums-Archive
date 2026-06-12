---
title: "Ubuntu 7.04 won't recognize drive partition..."
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by MrJoe83 on 2007-10-10
I use an external usb hard drive.  I partitioned it with Norton Partition Magic and installed Ubuntu 7.04 on the new partition.  Ubuntu runs great from the external hard drive.  My problem is I cant access the original partition of my hard drive which is where a bulk of my media files are kept.  I can access the drive I have all my windows stuff on and I can still get to the original partition from windows but not with Ubuntu.  What should I do?  The file system is NTFS if that helps at all.  Thanks.

---

### Post by LowSky on 2007-10-10
you need to download ntfs config tool in synaptic or use the add/remove program, the use the program to read/write to that partition

---

### Post by eph1973 on 2007-10-10
You should be able to read the files.  You should find your windows drive under something like /media/hda1.  Go to your /media directory, and you'll see something like hda1 (or sda1, or hdb1 or whatever partition it is that windows is installed).  From there you can copy the files to some other directory on your Linux partition, and change the permissions to what you like using chmod.

However, if you need read/write access, or you have a very large amount of files in various places all over your Windows partition, you need ntfs-3g.  If you want to use ntfs-3g, there is a [tutorial on how to set it up here]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G").

---

### Post by overlord.gaurav on 2007-10-10
Since you're on Feisty Fawn, it is very easy for you to have the read-write support.
Just do this:

```
sudo apt-get install ntfs-3g ntfs-config
```

Go to Applications >> System tools >> NTFS Configuration Tool.
Check both of the options, click OK and you're done!

---

