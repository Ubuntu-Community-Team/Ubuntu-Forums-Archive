---
title: "home partition crashed! how to recover"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by NT4.0 on 2007-06-23
For the first time in this half-year (I should have never done it in the first place, but this was just for testing purposes! damn) I popped in the XP CD to temporarily install Windows XP on a small 2G FreeDOS partition. My hard drive was partitioned in the following way: ubuntu system (ext3, 12 G), ubuntu swap (swap, 2 G), FreeDOS (fat32, 2 G), extended: [backup (ext3, 26 G), home (ext3, 140 G)]. Windows installation did not go well as on the next startup it said there was nothing to boot. I booted from the Ubuntu Live CD and in gparted the home partition was marked "unallocated"! I tried several ways but no luck. Is there an easy way to recover it? What software would you recommend?

---

### Post by HotShotDJ on 2007-06-23
STOP WHATEVER YOU ARE DOING.  Do not mount that partition.  Please standby.  I had a very similar problem in the past and successfully recovered the data on an overwritten partion.  Give me a few moments to get the information for you.

OK  -- here are the tools I used: [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") using [Recovery Is Possible Linux Rescue CD]("http://www.tux.org/pub/people/kent-robotti/looplinux/rip").

---

### Post by NT4.0 on 2007-06-23
HotShotDJ, I am not mounting this partition, I am using Ubuntu Live CD to get things done, like go online and access my USB HDD. I'll be looking forward to any help.

---

### Post by HotShotDJ on 2007-06-23
Ok... I edited my previous post with the information.  Good luck and I hope you are able to recover your /home partition!  Like I said, it worked for me.

---

### Post by NT4.0 on 2007-06-24
Restored! It took me some time to do it but now everything is working fine.

HotShotDJ, thank you for your help. TestDisk did not help me, it said the partition was probably damaged and it was not possible to recover it. However, looking at the second option you gave me I remembered I had a similar ISO called System Rescue CD (AFAIK it is based on Knoppix), and it turned out I had a CD with it. So I booted it and started Ranish Partition Manager, where I saw that the home partition was marked incorrectly and that's apparently why it had not been detectable. I marked it "type 83/linux ext" and it got mounted! Ever since it has been visible in all OSs but it took me a while to restore GRUB (unlike the partition image backup, I don't know any means to back up GRUB). The partition layout changed a little (home is now hda6 and not hda5) and I had to correct /etc/fstab but now it's up and running.

So the thing I've learned is, DON'T USE WINDOWS. Not only is it stupid but also aggressive (it wipes out your MBR without warning and may also damage your partitions if they are not its own). QEMU is the only place where this crapware may be allowed to run.

---

