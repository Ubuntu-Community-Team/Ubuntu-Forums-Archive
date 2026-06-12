---
title: "Grub Error 17"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by volksolwagen57 on 2007-12-03
I think this might be a common error. I checked it out on google and tried the widows repair console and typed "fixmbr" to get rid of grub. The only thing this did was delete grub (I think) nd not really fix mbr. I'm trying to install Ubuntu 7.10 amd64 and it hangs on the partitioner. Then I tried 7.04 amd64 and it installed but I'm still having the same problem. I'm kinda desperate because I have roughly 1,500 family photos I haven't backup up and about thirty home movies that haven't been backed up either. They are stuck in WIndows. Help!:confused::confused::confused::confused::confused:

---

### Post by volksolwagen57 on 2007-12-03
I forgot to mention that I have only one sata 500gb hard drive with a windows partition (ntfs) and I partitioned 360gb with ext3 and there are 8mb of unallocated space but I think my hard drive needs that so I won't touch it. Thanks in advance.

---

### Post by meierfra on 2007-12-04
Click on FixMBR in my signature. That will give you a couple of more options to  fix your MBR.  But I doubt that they will work, because fixmbr from the repair  console really should have  solved your problem.

If that did not work, boot from the ubuntu Live CD and see whether you can access your Windows files. There could be an icon for the windows partition on  the Desktop, If not look in "Places->Computer".

Also open a terminal in the Ubuntu Live CD (Applications->Accessories->Terminal) and post the output of 

```
sudo fdisk-l
```
("l" is a lowercase L)

---

### Post by froy02 on 2007-12-04
If you're only trying to recover windows for now you only did the first step, fix mbr, now get your windows installation disk and boot from it like you'll install it. When you get to the step where it says install or fix choose fix installation.

After that you may have to install grub again to get your ubuntu. 

Or if you want to recover your data boot from live cd and copy the data to another drive, like a usb drive maybe. Ubuntu can read both ntfs ans ext3/ext2 formats.

Lesson: Your data drive should not be your boot drive.  You can install all your operating systems in 1 drive and data in another so that you can lose all your OS's but still have your data.
I dual boot 2 desktops, 1 xp and ubuntu, and the other vista and ubuntu but my data is on separate drives.  I do not use the default /home folder in ubuntu nor do i use the default My Documents folder in windows.  So if i lose all my operating systems my data is intact.

---

### Post by alienexplorers on 2007-12-04
You could try the super grub disk or floppy to fix your MBR.  Follow the link in my sig.

---

### Post by quandary on 2007-12-04
See:
[http://ubuntuforums.org/showthread.php?t=576648](http://ubuntuforums.org/showthread.php?t=576648)

---

