---
title: "new ext3 partition, 5GB already gone? (and more)"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by Cruz on 2006-09-22
Hi,

this question is not clearly ubuntu, but I find that you get qualified answers here really fast. I just used SystemRescueCD for the first time to format a drive and create a fresh ext3 partition. And now it shows me that 5.8 GB of the partition is already used, although I can't see anything except  a small lost+found in the file system. Is this normal?

Ubuntu can handle ext3 partiton right? (Coz the default seems to be ext2)

And is there a way to pause an already started looong copy process and continue a few minutes later?

Thanks
Cruz

---

### Post by meng on 2006-09-22
Could be normal, is it a large partition?

---

### Post by p.i.m.p on 2006-09-22
Hi

ext3 is ext2 with a journal.. any recent linux distribution will most likely have support for it.. ubuntu sure does.. and it is backwards compatible with ext2
as for ur second question, try typing in 
```
sudo find <path to drive> -size +100M
```

This will look for files greater than 100 mb in the drive so that u can get a better idea of what might be eating up all that space.. u can modify 100M with anything that you think is better suited

---

### Post by Cruz on 2006-09-22
Yes the partition large, it's 120GB. I already copied it full with games and isos so I don't think looking for large files makes sense anymore. :( However, I did a visual check on the partition right after the creation and like I said all I could see was a little lost+found directory. Must be the journaling really. 5GB off my drive is a pain though, could put 2 or 3 more games on it. ;)

---

### Post by bulldog on 2006-09-22
You used a Rescue disk,what was it supposed to rescue??

If you want to format a whole hdd you better use gparted and no rescue disk.

---

### Post by Cruz on 2006-09-22
The system is running XP and is in the middle of a metamorphosis to ubuntu right now. I used the SystemRescueCD just because I always wanted to check it out why is that so bad? It's a nice and quick live CD distro for partitioning and imaging.

---

### Post by bulldog on 2006-09-22
Well you've seem to lost 6GB and I'm curious where it went:) 

If the rescue disk made a hidden partition with a rescue of your old system,you know where it has gone.

But I'm not suggesting a rescue cd is bad,but I understood you wiped the entire hdd and lost 6GB in the mean time.

---

### Post by Cruz on 2006-09-22
Yeah alright you are thinking in the right direction but I don't think that's the case. Before the drive was one big 120 GB NTFS partition full of games. I explicitly formatted it and created a fresh 120 GB ext3 partition. You think it "rescued" all my stuff over the formating and partitioning into a 6 GB hidden place? :)

---

### Post by maaronB on 2006-09-22
I am new to ubuntu but I know that on some other distros 5% of the filesystem is hidden and only accessable by the root user.  Just going by the numbers (6GB missing on 120GB drive) I would say that is what is happening here.

---

### Post by bulldog on 2006-09-22
There are wonders you know :D  but I don't think so really.

But if the hdd was formatted you can't lose 6GB?

I should format it again with a proper application,to see if it happened again.

---

### Post by bulldog on 2006-09-22
> **maaronB said:**
> I am new to ubuntu but I know that on some other distros 5% of the filesystem is hidden and only accessable by the root user.  Just going by the numbers (6GB missing on 120GB drive) I would say that is what is happening here.


Could be,I've never heard of such a thing,but I know nothing.

Only what should be the purpose of such a thing?
You can't login as a root and if you do sudo you can access everything.

Only thing I can think of that it's the /root space.

But it's certainly possible.

---

### Post by podunk on 2006-09-22
Drive manufactures sell the drive as XXX gigabytes - but OS's treat it slightly differently, they don't define a gigabyte or a mega byte the same way. One uses octal and the other uses base 2.

So your hard drives "selling" size will always be a bit bigger than what you end with after formatting. You "lose" about 73 megs (octal!) per gig.

---

### Post by Cruz on 2006-09-22
QTparted isn't proper enough for you? Alright my friend. I just threw away more than an hour copying work just to experiment around. I did use QTparted again from the SysResCD and created an ext2 instead of ext3 partition this time. And now 1.8 GB were taken. As far as I know there is no journaling in ext2 so that does it! I'm switching to Knoppix now and starting over.

---

### Post by maaronB on 2006-09-22
> **bulldog said:**
> Could be,I've never heard of such a thing,but I know nothing.

Only what should be the purpose of such a thing?
You can't login as a root and if you do sudo you can access everything.

Only thing I can think of that it's the /root space.

But it's certainly possible.

Not that it matters because I don't think that was your problem, but the reasoning behind the 5% is for network servers in a buisness setting.  That way it is impossible for a normal user (or hacker with access to a normal user account) to fill the hard drive.  Making it easier for the admin. to clean it up.

Though I admit it doesn't make much since for a desktop Computer, espically now that storage is so cheap.

---

### Post by zekopeko on 2006-10-19
> **Cruz said:**
> QTparted isn't proper enough for you? Alright my friend. I just threw away more than an hour copying work just to experiment around. I did use QTparted again from the SysResCD and created an ext2 instead of ext3 partition this time. And now 1.8 GB were taken. As far as I know there is no journaling in ext2 so that does it! I'm switching to Knoppix now and starting over.

try this in terminal if it isn't too late and you have switched to Knoppix.

```
tune2fs -m 0 path/to/your/partition
```

this will remove the root space

---

### Post by Cruz on 2006-10-30
> **zekopeko said:**
> tune2fs -m 0 path/to/your/partition

Hey thanks that's an interesting suggestion. Do you know what those reserved blocks are there for? It doesn't say anything about it in the man page.

---

### Post by kinematic on 2006-10-30
the file system itself takes up space too.

---

