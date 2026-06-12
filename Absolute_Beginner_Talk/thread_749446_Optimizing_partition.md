---
title: "Optimizing partition"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by bishamon on 2008-04-08
Hi

Anyone here got any recommended options on format the file systems? I have a said 500G hdd and it is meant for storing movies. On average each movie is said to be 700M. So if I use the default options on mkfs.ext3, I see almost 5G unusable, taken up by the journal and inodes, even before I start transfering files. 

I estimated that I won't go beyond 500K of files in this HDD, so I do a "*mkfs.ext3 -N 500000*" on that partition. When I do a tune2fs on that device, what bugs me is the following information

> Inodes per group:         448
Inode blocks per group:   28


I did a test of coping some files and they told way too long! A 500M file can take close to a minute before finishing the job! Any parameters that I have forgotten to add in to optimize it? On a NTFS, I will always format the hdd to a 64K file cluster. On ext3, I'm trying to have a better understanding of the inode settings. 

Any experts here willing to shred some light on this? 

bishamon

---

### Post by njparton on 2008-04-09
XFS offers much better performance than ext3 :)

---

