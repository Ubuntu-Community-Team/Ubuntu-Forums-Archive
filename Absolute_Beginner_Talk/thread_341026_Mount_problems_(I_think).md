---
title: "Mount problems (I think)"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by Squeek on 2007-01-18
Ok, so I'm a total noob, just taken the linux plunge.  Now, I have installed ATI drivers (although ATI Control gives me an error message if I try to launch it), I have installed the newest Firefox, the newest Adobe Reader, whatever.  However, Ubuntu 6.10 isn't seeing my Windows partition or my two other hard drives.  This would be very useful, since I store my pictures, music, etc. on those drives.  What is the best (read: easiest) way to get Ubuntu to see those drives?
Thanks in advance for the help,
Squeek

---

### Post by Squeek on 2007-01-18
bump

---

### Post by jd65pl on 2007-01-18
Its not a mount problem as such, only that you haven't mounted them. You should check your file system types on your windows disks as ntfs isn't really great for read/write support via linux. The best option IMHO for sharing files between windows and linux is a fat partition.

See this for nfts read only [https://wiki.ubuntu.com/mountNTFSreadonly?highlight=%28ntfs%29](https://wiki.ubuntu.com/mountNTFSreadonly?highlight=%28ntfs%29)

---

### Post by Squeek on 2007-01-20
Ok, so I went through the listed steps, and I chmod 777 the drives, but when I open them through the GUI there are no folders in the drive.  Any ideas?

---

### Post by confused57 on 2007-01-20
Here's an excellent guide to mounting partitions:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

Might want to read this thread:
[http://www.ubuntuforums.org/showthread.php?t=341609](http://www.ubuntuforums.org/showthread.php?t=341609)
didn't get any feedback from the OP, so don't know if it worked or not...

---

