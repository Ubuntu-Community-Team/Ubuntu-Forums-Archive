---
title: "What's the distinction between 'free' and 'available' disk space?"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by BetterSense on 2008-03-27
I just got a banner that said I have 99% full disk. Surprise to me. I went to System Monitor and it says I have 192MB free, but only 1.3MB available. What's the difference? Why do I have disk space that is free, but not available? Any ideas why my disk became full (temporary files, or something accumulaing). I only have a 4GB SSD on this machine.

---

### Post by wolfen69 on 2008-03-27
do in terminal:
```
sudo apt-get clean
```
then
```
sudo apt-get autoremove
```
this may free up some space.

---

### Post by BetterSense on 2008-03-27
Thanks that helped a lot; now I have 700MB free and 500MB available. But still, I don't understand what's the distinction. Before I cleaned and autoremoved, why was it saying that the space was free, but not available?

---

### Post by meindian523 on 2008-03-27
I guess 
free==>non-partitioned while
available==>free space within already created partitions.

But this seems unlikely because no one usually has only 500 MB non-partitioned space,it's usually in GBs.

---

### Post by mcdan on 2008-03-27
The ext3 filesystem reserves an amount of the total space for root. If some user (or daemon) fills the disk then a login couldn't be possible anymore. So even root couldn't login anymore to fix it. Therefore ext3 reserves an amount of 5% (default) of the filesystem for the root user to prevent it (it doesn't work if root fills the disk).

Available space is now the total free space including the reserved space for root.
Free space is the free space that you as a user can fill



from:
[https://answers.launchpad.net/ubuntu/+source/gnome-system-monitor/+question/8609](https://answers.launchpad.net/ubuntu/+source/gnome-system-monitor/+question/8609)

---

### Post by BetterSense on 2008-03-27
It's ext2.

---

