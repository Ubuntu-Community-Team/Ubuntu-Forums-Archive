---
title: "Partition Harddrives/Formatting Harddrives"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by Josh1 on 2006-12-16
Hi all,
What tool is the best for formatting harddrives in Ubuntu? I want to use a couple to store files. How would I go about formatting a harddrive then setting one big partition on each to store files? I would prefer to create them in NTFS as they are mainly going to be used to share the files with friends (as the files are a little to big to put onto a DVD).

I have heard of GPart/GParted or something but can not find much information on this, or is there a better tool to do to job?

Cheers,
Josh

---

### Post by Westies on 2006-12-16
I like GParted myself.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by Josh1 on 2006-12-16
Cheers!
I loaded the iso onto a CD, booted into the LiveCD and formatted the drive using Fat32. How do I show the drive in Ubuntu?

---

### Post by bodhi.zazen on 2006-12-16
You have to mount it or add an entry in fstab.

Mounting and permissions depends on the file system:

_Windows:_

For read-write: [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)

vfat (FAT) use umask=000

See also [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

---

