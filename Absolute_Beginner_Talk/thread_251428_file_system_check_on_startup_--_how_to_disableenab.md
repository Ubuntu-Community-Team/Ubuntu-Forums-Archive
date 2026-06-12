---
title: "file system check on startup -- how to disable/enable"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by sqlplus on 2006-09-05
Hi,

When I originally installed ubuntu, when booting the system, the filesystem would not be checked every time. I think every 30 times or so.  

Now, after a install of kubuntu (into different partitions), the system does the filecheck on each system startup.  It takes a long time, esepcially for the check of the windows partitions (one fat32 and one ntfs). 

How can this startup behavior be adjusted? Any ideas why it would have defaulted to check the fs for my new install?

Thanks in advance!

---

### Post by dcsleeps on 2006-09-05
> **sqlplus said:**
> Hi,

When I originally installed ubuntu, when booting the system, the filesystem would not be checked every time. I think every 30 times or so.  

Now, after a install of kubuntu (into different partitions), the system does the filecheck on each system startup.  It takes a long time, esepcially for the check of the windows partitions (one fat32 and one ntfs). 

How can this startup behavior be adjusted? Any ideas why it would have defaulted to check the fs for my new install?

Thanks in advance!

Hi sqlplus,

I don't have much time at the moment, but I'm having the same issue and have come across two possible fixes for this. The first one (and likely best) is this recent post by rumli [here]("http://www.ubuntuforums.org/showthread.php?t=187191")

The second, and more general, fix is a blog entry entitled ["Tuning the Filesystem Check at Bootup"]("http://ubuntu.wordpress.com/2005/10/12/tuning-the-filesystem-check-at-bootup/") over at the Ubuntu Blog. The entry describes how to disable the filesystem check on reboot, permanently, or set it to occur once per day, week, etc.

Hope this helps

---

### Post by sqlplus on 2006-09-05
thanks for the links, they look very helpful!

I think that I figured out how to solve my specific issue.  What was taking a long time was the checking of the "other filesystems" (e.g., my fat32 filesytem that I used to share files between win and linux, seen during bootup as "Checking all filesystems".   This is controlled by the last column in /etc/fstab.   If that value is non-zero, say 1 or 2, that filesystem will be checked on startup.   Trying to make the change now... will post again if this doesn't work...

---

