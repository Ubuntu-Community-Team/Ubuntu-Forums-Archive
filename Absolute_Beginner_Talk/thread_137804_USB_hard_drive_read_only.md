---
title: "USB hard drive read only?"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by B7may on 2006-02-28
I am very new to Linux.  I have just installed Breezy 5.10 and am happy with it.  I am planning on using it as a file server with other windows XP system.  So far everything works great.  I have a 160 GB USB drive.  I plugged it into the machine, and it works fine.  However, I only have read access.  How do I change it so that everyone can have total access?

Thanks
Brian

---

### Post by suRoot on 2006-02-28
What kind of filesystem is on the USB Drive?  Better way to ask it, did you format it under XP?  If so, you're probably using the NTFS filesystem which is only safely supported as read-only under Linux.

---

### Post by B7may on 2006-02-28
It was formatted under windows and is NTFS file system.  Should I reformat it under Linux?  If so, how would I go about doing that?

Thanks
Brian

---

### Post by Sutekh on 2006-02-28
If you want to have write access from both Windows and Ubuntu, reformat it with FAT32.

You can use GParted in Ubuntu.
```
sudo apt-get install gparted
```Wil install GParted for you.

I haven't had any experience using it, but I do know that the partition must be un-mounted before you can do any partitioning to it

Here's gparted's site (some screenshots)
[http://gparted.sourceforge.net/screenshots.php]("http://gparted.sourceforge.net/screenshots.php")

Alternatively search the forum for 'gparted' there is a alot of info on how to use it.

---

