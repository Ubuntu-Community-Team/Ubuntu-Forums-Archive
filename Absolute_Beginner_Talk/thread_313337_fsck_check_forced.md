---
title: "fsck check forced?"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by P235 on 2006-12-05
Hi, I rebooted my laptop and noticed that a check of some sort was being done on my partitions?  That's what I gleaned from the messages anyhow.  One of my partitions failed the test and I was told to check /var/log/fsck/checkfs:

> Log of fsck -C -R -A -a 
Tue Dec  5 19:46:13 2006

fsck 1.39 (29-May-2006)
/dev/hda2 has been mounted 30 times without being checked, check forced.
Error reading block 66045 (Attempt to read block from filesystem resulted in short read) while doing inode scan.  

/dev/hda2: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
fsck died with exit status 4

Tue Dec  5 19:46:22 2006
----------------

Is this as ominous as I think it is?  Also, what must I do?

---

### Post by pay on 2006-12-05
Try doing what it says ```
fsck 
/dev/hda2
```

---

### Post by P235 on 2006-12-05
I just tried, but I get this:

> fsck 1.39 (29-May-2006)
e2fsck 1.39 (29-May-2006)
/dev/hda2 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted.


As I recall, I set up hda2 as my /home.  How do I unmount hda2 to run fsck?

---

### Post by pay on 2006-12-05
Try loading a liveCD and then running that command.

---

### Post by inabsolutes on 2006-12-05
You could also reboot and run ```
fsck /dev/hda2
``` from the root prompt that it gives you.  Your home partition shouldn't be mounted.  I've had to do this as well with my separate root partition.  If it is mounted, then I would go with the Live CD.

---

### Post by P235 on 2006-12-05
Thanks, the Live CD did the trick.

/hda2: 14718/2101152 files (1.0% non-contiguous), 1189473/4194973 blocks.

I'm not sure what it means, but as the test finished I get the feeling that nothing is wrong.  Now I feel incredibly newbish :neutral:

---

### Post by pay on 2006-12-05
It says that to me every time I boot up. Most the time I can ignore it but once in awhile it will fail and I will have to do what I suggested to you.

---

### Post by d3v1ant_0n3 on 2006-12-05
The 1.0% noncontiguous bit mean 1.0% fragmentation. Which is basically nothing to worry about.

fsck will run on every 30th boot automatically and check the file system for errors. You get used to it after a while, although it * always* seems to happen to me when I just want to check something quickly on the computer:p

---

### Post by P235 on 2006-12-05
I see, thanks all!  Will I ever have to defrag at some point?

---

