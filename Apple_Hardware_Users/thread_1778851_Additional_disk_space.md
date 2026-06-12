---
title: "Additional disk space"
date: 2011-06-09
forum: Apple Hardware Users
---

### Post by vanhornd on 2011-06-09
Ubuntu currently uses 20 G for its filesystem.  I have allocated an additional 215 G that Ubuntu recognizes on its desktop as additional space.  I would like to integrate the 215 G into the filesystem, but do not know how to proceed.  The 215 G is *not* temporary.  It is blank space on my hard drive.  I just want to make the Ubuntu partition bigger.  Can anyone help me?  Thank you.

Doug

---

### Post by FormatSeize on 2011-06-09
Yes, you can use GParted. The way that I do it is through [Hiren's Boot CD]("http://www.hirensbootcd.org/download/"). Now this CD has a *lot* of other stuff on it used for various purposes, and you can read about all the other stuff that this CD can do it if you want.
But anyway, you boot from the disk, which will present you with a pretty drab looking menu. The way to get to GParted will be by entering the "dos programs" section, and you should be able to find your way from there. 
Once you get there, you will get a GUI that's pretty straightforward which will allow you to extend your Ubuntu partition into the free space. Exit, take the CD out, reboot, and you're golden.

---

### Post by oldfred on 2011-06-09
Depending on whether the space is adjacent to your system partition it may or may not be easy to expand your / (root). I prefer smaller root partitions for slightly faster system response and separate /home or /data partition for data. You could mount the extra space a new /home after moving your current data in /home or just move some data folders and mount the partition and link the data partitions back.

These are really the same just using different commands. One may make more sense than another so I post all of them:
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Shared /data -see post #5 oldfred Except I now mount in /mnt not /usr/local/fred
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)
Another way to share:
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)
Partitioning basics with some info on /data older but still relavent
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

---

### Post by bdentremont on 2011-06-10
> **oldfred said:**
> ... You could mount the extra space a new /home after moving your current data in /home or just move some data folders and mount the partition and link the data partitions back. ...

I agree with oldfred.  I'd keep the partition separate and either copy your home directories there and mount it to /home or mount it to /mnt/{something} and link directories to it with the "ln" command.  I do a little of both, as described below.  Permanent mounting of partitions is done in the /etc/fstab file and you should find plenty of documentation on that, including in the links that oldfred posted.

My / is only 15GB and I've never needed more than 9GB of that for any of the software that I wanted to use.  Typical Linux software is light.  The largest partition of my disk is /home, which gets well used with photos, videos, laboratory data, etc.  I also have partition /mnt/mac which is NFS (mac file system) with my OS X home directory.  Subdirectories in this get linked into /home as needed for stuff that I want to share between OSs.  Once setup, either the linked directories or separate home is pretty seamless as a user.

---

### Post by vanhornd on 2011-06-10
Thanks for the reply! It makes sense to me. I appreciate your help.

---

