---
title: "Partition troubles dual boot"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by Mular on 2007-12-16
Ok I made a mistake when I was first installing ubuntu I accidently picked the wrong drive as my linux swap file.. 

At first it wasn't a big deal, but now windows isn't letting me see this drive. It comes up in device manager as Local Disk > NTFS file system > Health Unknown file system..

Is there anyway to get windows to see this drive again?? 

I had to reformat windows today because, well doesn't matter but I did, prior to reformatting I installed a program that let me see linux filesystems under windows. I don't remember where I found that..

Any help would be really appreciated

Mular

---

### Post by Existentialist on 2007-12-16
In order for windows to see it again without anything extra, it would need to be formatted NTFS.  Was there data on the partition you needed off?  If not you can just reformat it to NTFS.

---

### Post by chuckyp on 2007-12-16
e2fs explorer or something like that I believe is the name of the windows program.  Just search for windows ext3 in google and you will get a bunch of results.

---

### Post by Mular on 2007-12-16
Yeah sadly there is about 100gigs of data and I don't have room to do it.. maybe I can just play with partitions in gparted to fix it.. hrm

---

### Post by Existentialist on 2007-12-16
There is a program for linux called testdisk you can install:

>sudo apt-get install testdisk

It is able to find old partitions and assuming you did not format that partition the data should be pretty easy to recover.  I'm sure there are good posts somewhere in these forums for how to use it as it isn't graphical.

---

