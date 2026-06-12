---
title: "&quot;No free space&quot; error with cfs encrypted directory"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by t0p on 2008-03-31
Some time ago, I used cfs (Crypto File System) to create an encrypted directory, and stored various files there.  Today, I created another encrypted directory, and when I went to store files there, I got a "no free space" error.  I checked the first encrypted directory, and found that I got the same "no free space" error there too.

I really don't get this, as my computer's hard disk isn't full.  I give command
```
df -h
```
and I get the output
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             8.4G  4.6G  3.4G  58% /
varrun                125M  112K  125M   1% /var/run
varlock               125M  4.0K  125M   1% /var/lock
udev                  125M   76K  125M   1% /dev
devshm                125M     0  125M   0% /dev/shm
lrm                   125M   34M   91M  28% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1             9.8G  8.4G  1.4G  86% /media/sda1

```
From this, I can see that the filesystem the encrypted directories are situated in (/dev/sda2) is only 58% used, and there's still 3.4G available.

Can anyone shed light on this?  And suggest how I can go about fixing this problem?

---

### Post by t0p on 2008-03-31
Ah... some weird stuff going on here...

I've been getting the "no free space" errors when trying to move files into the encrypted directory (well, the cattached directory, to be precise) via the GUI.  I've just tried moving files via the CLI, and I was able to store the files, no problem.

So, the problem isn't that there's no free space... it is that Gnome is *claiming* that there's no free space...

The problem isn't as major as I thought at first - I can store files in the encrypted directories by using the CLI - but I still would like to know: **why is the GUI claiming there's no free space?!!**

Any ideas, people?

---

