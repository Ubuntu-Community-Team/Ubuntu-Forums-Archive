---
title: "Help with formatting extra free space"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by stevenash on 2006-05-21
I recently installed Ubuntu on a 250 GB drive.  I used 31 GB for the total installation (10 for the /root, 20 for /home, 1 for swap).  When I was installing Ubuntu, I tried formatting the remaining 219 GB as FAT32, but apparently that is too large.  So I just left it as free space to come back to later.

Now that Ubuntu is installed, I want to format the rest of the free space.  Basically, I want some space available that Ubuntu can both read and write to, then the rest I just need Ubuntu to read.  So I was thinking about making a 19 GB FAT 32 partition and then the last 200 GB an NTFS partition.

The problem is, I don't know how to do this in Linux.  I suppose I could do it easily with Partition Magic in Windows, but I'd rather learn something new in Linux.

Can anyone tell me how to do this?

Thanks!

---

### Post by aysiu on 2006-05-21
What's the fascination with FAT32?

Why not just format it as Ext3?

Take a look at [this post](http://www.ubuntuforums.org/showthread.php?p=1039386#post1039386), and just forget all that stuff about Windows--the same principle applies in this situation. It just probably won't be /dev/hda1.

---

### Post by stevenash on 2006-05-21
I've been told numerous times that if I want to share files between Windows and Linux (and have Linux both read and write to the partition), you should use FAT32.  That's why I chose it.  I have to say, I'm still lost though.

---

### Post by aysiu on 2006-05-21
You can use [http://www.fs-driver.org](http://www.fs-driver.org) to read/write Ext3 from Windows.

---

