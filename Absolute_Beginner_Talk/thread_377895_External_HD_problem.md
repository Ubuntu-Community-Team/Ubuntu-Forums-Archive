---
title: "External HD problem"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by teruokun on 2007-03-06
Hello everyone,

I have a 280GB FAT32 external HD that I use a lot.  It's been working great with Ubuntu, but now there's a problem with it.  It no longer mounts and even windows computers won't show it. I've tried 

fsck.vfat -at sdi

and it says there is no such file or directory.  I even tried fixdisktable-0.3 but it finds no partitions.  It's only about 6-months old and it's most likely not worn out because of use or age. and some of the files on there (like my girlfriend's photo repository) cannot be replaced.  Are there any good tools for linux that I could use that might be able to help me reclaim at least some if not all of the files?  Currently my gf's windows computer is in the shop and I only use ubuntu on my laptop.

Thanks for all the help!

---

### Post by compiledkernel on 2007-03-06
You can try recoverdm -- [http://www.vanheusden.com/recoverdm/](http://www.vanheusden.com/recoverdm/)

Takes a little getting used to, and can require up to a number of days of machine time (easier just to devote a machine to it). 

Additionally you can try to use ddrescue as well. 

[http://www.gnu.org/software/ddrescue/ddrescue.html](http://www.gnu.org/software/ddrescue/ddrescue.html)

Those two are the prizes of the Data recovery field IMHO.

---

