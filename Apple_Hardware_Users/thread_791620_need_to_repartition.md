---
title: "need to repartition"
date: 2008-05-12
forum: Apple Hardware Users
---

### Post by emale07 on 2008-05-12
A few weeks ago I partitioned my HD with Boot Camp to allow for an Ubuntu install.  About a week later I used GParted to enlarge the partition.  Now I find that I need the space back.

I booted the LiveCD and ran GParted, and was allowed to reduce the size of my Ubuntu partition.  However, I was not allowed to enlarge the size of my Mac partition.

Any ideas about how I can reclaim the space?

---

### Post by hermes0710 on 2008-05-12
I am not familiar with Mac but i do know that gparted for resize should only be used for safety only on linux partitions. Otherwise it might mess up your other os... Doesn't Mac provide any partition tools?

---

### Post by emale07 on 2008-05-12
I would imagine they do, but I thought I'd start here.  

Can anyone recommenda  good Mac partition tool that won't cost an arm and a leg?

---

### Post by hermes0710 on 2008-05-12
> **emale07 said:**
> I would imagine they do, but I thought I'd start here.  

Can anyone recommenda  good Mac partition tool that won't cost an arm and a leg?

:lolflag:

---

### Post by Jammy4041 on 2008-05-12
If you want to resize you HFS+ Partition, you don't have to pay money.

[http://ubuntuforums.org/showthread.php?t=89960](http://ubuntuforums.org/showthread.php?t=89960)

---

### Post by cyberdork33 on 2008-05-12
There are no open source tools that can "grow" hfs+, only shrink.

You can use the OSX commandline utilities ('diskutil resizeVolume'), or if you have Leopard, Disk Utility (running from the install disc) should be able to resize the partition.

---

### Post by DomnizkyDesign on 2008-05-12
careful careful. I just had this problem yesterday.

I used the 8.04 disc to shrink my Ubuntu partition, but couldn't enlarge my OS X partition.

So I decided to used Drive Genius. Not Drive Genius 2, the first one. Got it on clearance from the Office Depot I work at for Five bucks.

When I wanted to enlarge the OS X partition, it showed that I needed the free space to be right next to the partition I wanted to enlarge. how it went on the drive map was this:

APPLE FREE (5MB) <-Not it, just an artifact from something or other...
MACINTOSH OS X PANTHER (18GB) <-The partition i wanted to enlarge...
UBUNTU804 (5GB) <-After shrink...
APPLE FREE (5GB) <-The target free space.

So, i wanted to use the program's "Shift" feature to switch the Ubuntu partition with the free partition, so I could use the extra space on OS X. I did this because I didn't want to touch my OS X partition just in case anything went wrong...

The shift went by quickly... showed the partitions had been swapped...

And I could no longer boot into OSX. When I tried to boot into Ubuntu it didn't work either.

So now my dual-boot iBook is just a regular-old Ubuntu-iBook.

---

### Post by mariguango on 2008-05-13
Please use apple progs to work with apple partitions and linux soft - for linux partitions. 
You don't need third party software if you on leopard - just use Disk Utility, and you may google for comand line options.

May be this [link help]("http://ehmac.ca/anything-mac/43204-restore-efi-partition-proper-bootcamp-operation.html") you solve your problem?

---

### Post by emale07 on 2008-05-14
> **cyberdork33 said:**
> There are no open source tools that can "grow" hfs+, only shrink.

You can use the OSX commandline utilities ('diskutil resizeVolume'), or if you have Leopard, Disk Utility (running from the install disc) should be able to resize the partition.

I'll try this this evening and report back.

Thx.

---

