---
title: "2000/XP/Ubuntu Problem"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by underdog on 2006-05-18
Hi, I have another multi-boot problem, and I have searched extensively and can't find an answer

OK, I bought a laptop with XP Home on it. It had two partitions on the hard drive (so i have a C: and D: drive). I resized my hd (the C: partition) and made room for my root and swap partitions. I then installed Ubuntu, and it detected XP and I had a happy dual boot. 

Next, I guess I screwed up. I installed Windows 2000 to the D: drive. Now, in GRUB, when I try to boot one of the XP options, it either goes to 2000 or just dies saying it can't load 2000 for some reason. I've tried to edit boot.ini to add an xp option, but I'm not sure if I'm doing that right, either. I basically just want XP and Ubuntu to work, so if i have to kill 2000, thats fine. Thanks in advance.

---

### Post by tonyr on 2006-05-18
In general for dual boot installations like XP/Linux, you should install all of the 
Windows OSen first, then Linux.  You can regenerate the GRUB boot record
a couple of ways, which I can't recall at the moment, but by the time you see this
someone else may have already posted them.  If not,  I'll search them up
and post here.

---

### Post by tonyr on 2006-05-18
Here's one. It says Breezy 5.10 but should work for Dapper, too.
[URL="http://www.ubuntuforums.org/showthread.php?t=76652&highlight=grub+recover"]
http://www.ubuntuforums.org/showthread.php?t=76652&highlight=grub+recover[/URL]

---

### Post by underdog on 2006-05-18
If it helps, in linux I hda2 is my nt drive, i think hda1 is my xp drive.

In my grub menu.lst file, here are some details:

Ubuntu boots from hd0,2

xp: hd0, 0
2000: hd0, 1

I'll give more details about each if needed

---

### Post by tonyr on 2006-05-18
...and here's the other one:
[RecoveringUbuntuAfterInstallingWindows]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows")

---

