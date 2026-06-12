---
title: "Read-only filesystem?"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by hathead on 2006-03-22
Whenever I try to write to /media/BUSLINK (/dev/sda1) it says I don't have permission. In /etc/fstab I have:

/dev/sda1 /media/BUSLINK ntfs rw,noexec,nosuid,nodev,uid=1000,gid=1000,umask=0000 0 0

I can write to the HD fine under Windows (this PC). Also, it may be worthy to note that everything was working fine until the drive got formatted under Windows.

Also, this is completely unrelated, but whenevr I type 'users' it has my account listed twice -- slippeh slippeh. And when I type 'uptime' it says 2 users. Why does that happen?

---

### Post by aysiu on 2006-03-22
NTFS is read-only from Linux. Microsoft wants it that way.

There are programs to change that, but they're experimental right now. For more info, go [here](http://www.ubuntuforums.org/showthread.php?t=142481).

---

### Post by hathead on 2006-03-22
Oh, I didn't know that. Will 'sudo mkfs -t ext3 /dev/sda1' work on both Linux and Windows? Or what else should I do.

Thanks a lot

---

### Post by aysiu on 2006-03-22
Is the data on /dev/sda1 important to you?

If not, you can format it as FAT32 and share data between both Linux and Windows.

Or you can format it as Ext3 and use [a special driver](http://www.fs-driver.org/) to be able to read/write it from Windows.

---

### Post by hathead on 2006-03-22
There is no data on it. I formatted it under Windows a few days ago and haven't put anything on it since. I'm trying to transfer files from my Linux box->HD->Windows. I'll try the Ext3 driver and see if it works. If not, I'll go for FAT32.

Thanks a lot aysiu.

---

