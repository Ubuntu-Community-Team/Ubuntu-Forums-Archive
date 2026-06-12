---
title: "Removing Ubuntu on a duel boot system"
date: 2006-09-17
forum: Apple PPC Users
---

### Post by bonniejonnie on 2006-09-17
So this isn't really a pro-Ubuntu question... but there seem to be a lot of Ubuntu/Mac OS X experts here.

Basically I tried Ubuntu, and didn't like it. The lengths you have to go to to get things to work is just too much. So... I booted the Live CD (6.06) and used parted (sudo) at the command line to rm the Linux partitions. All these partitions are now gone and I'm left with 9.something GB of unallocated free space at the end of my hard disk. The plan was then to use parted to resize (upwards) the Mac OS X partition and get back all that disk space. However, I get the error:-

> Unable to satisfy all constraints on the partition.

What does this mean? Am I going about this in entirely the wrong way?

---

### Post by jfmbp on 2006-09-17
Henk Koster has made a detailed note about this -- thanks hajk

[http://www.xs4all.nl/~hajk/](http://www.xs4all.nl/~hajk/)

---

### Post by bonniejonnie on 2006-09-17
Thanks, but the article you refer is too technical for me, a Linux-amateur. It also talks about Boot-camp... I'm a PowerPC boy.

Are you aware of any notes more specific to PowerPC or any idea why parted would throw me such an error? All I'm trying to do is grow an HFS+ partition into free space... can parted fundamentally do this?

---

### Post by bonniejonnie on 2006-09-17
Ah ha... here's what I needed to know...

"Parted can only shrink HFS and HFS+ filesystems."

I guess it's a reformat then. Unless anyone else has some bright ideas.

---

### Post by hajk on 2006-09-17
You can always make the 9GB into a separate HFS+ partition with (g)parted, at least the space isn't lost in that case.
There could also be a tool in OS X to reclaim unallocated space, but I'm no OS X expert...

---

### Post by bonniejonnie on 2006-09-17
Okay... well parted can't create HFS+ but it can do HFS... no doubt I can then use OS X's Disk Utility to format it to HFS+. Who knows what the difference is.

I can't find any tool to reclaim unallocated space. So the above seems like the best option, short of a total reformat (I really don't have the energy to do that though).

Cheers.

---

### Post by stevenincleelum on 2006-09-20
iPartition is the tool!

---

