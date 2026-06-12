---
title: "Ubuntu startup delays"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by patalaveera on 2007-02-19
Hi,

I recently installed Ubuntu 6.10 on my laptop. Every time I start
ubuntu, it does a complete check of all Windows and Linux partitions.
My laptop vendor has created a recovery partition which is a FAT
partition and it takes awfully long to perform check on this
partition. It literally takes 10 minutes to boot up Ubuntu.

Is there a way to disable the hard disk check?
I tried a few things with tune2fs, but it did not work.

---

### Post by patalaveera on 2007-02-19
I fixed it. Although it is a really ugly hack, it does the trick.
This is how I fixed it:
I dug into init.d to see that there was a checkfs.sh running each time.
In that, saw that if a file /fastboot exists, it skips check, but at
the end, it removes the file /fastboot. I stopped it from doing that,
created a file /fastboot and it decently boots up.

but can someone explain why tune2fs is not working on 6.10?
when I pass it parameters, it keeps showing the usage help, even though all parameters are correct!

---

### Post by drs305 on 2007-02-19
I am a newbie but I seem to recall that my machine did the same thing. I edited the /etc/fstab . I don't know the mechanics but the last digit on the line for some partitions was higher than 1 and was forcing a disk or partition check. I changed that number to a 0 and now the disk gets checked about every 30th boot or so.

Example from fstab:
old:
UUID=eff10139-bf00-4f71-acb4-72a6cad24292 /media/hdb6 ext3 defaults 0 3
revised:
UUID=eff10139-bf00-4f71-acb4-72a6cad24292 /media/hdb6 ext3 defaults 0 0


The last 1 in the line used to be a 3 or something and generated a check. I'm an idiot at Linux but perhaps I've given you enough to be able to do a competent search on the forums for the correct background.

---

### Post by tomazw on 2007-02-19
drs305, you are right, I also had this problem:

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by patalaveera on 2007-02-20
Thanks!

---

