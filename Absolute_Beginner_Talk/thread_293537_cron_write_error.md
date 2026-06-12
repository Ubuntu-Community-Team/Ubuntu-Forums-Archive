---
title: "cron write error"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by ramshorn on 2006-11-05
The answer to this is no doubt obvious, but after considerable searching I have been unable to find a solution
in the existing threads. I recently installed an external 300GB hard disk,
connected to my computer running Dapper Drake via usb2. The problem is that I cannot write to this disk with a cron job. As an example, a cronfile with
the single line:

42 10 * * 0 touch /home/c/test

works just fine, creating the file test. Yet if I change the cronfile to

50 10 * * 0 touch /media/SEA_DISK/test

the cron job evidently fails, as no file is created. Moreover, from the terminal I can run the command: touch media/SEA_DISK/test successfully. 

Checking permissions using "Properties", 
/media and everything under it is 777 (a little like "turtles all the way down"). And my fstab has the following entry,

/dev/sda1       /media/SEA_DISK vfat    users,owner,rw,umask=000 0 0

I initially suspected that cron might run under a different user, and that that was the source of my problems. But at this point, it looks to me that everyone, including a mouse scampering across my keyboard, has write access to /media/SEA_DISK. Moreover, when I run, ps aux|grep cron I can see that cron is running. I'm at a loss as to where to look next.

---

### Post by ramshorn on 2006-11-05
So I reformatted the hd with ext3, and removed the relevant line from my fstab, and cron can now write to my external hd. I suspect that reformatting the hd is what fixed the problem, and that the fstab edit was superflouous. 

A little history, for those who might have a similar problem: I purchased the SeaGate hd in question new about a month ago, and installed it on a Windows 98 box, while I was waiting for a "new" computer from retrobox to arrive (said computer now running ubuntu). The advice given elsewhere on these forums that ext3 is preferable to fat32 if one has a choice sure worked for me.

---

