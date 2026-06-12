---
title: "Ubuntu install stops at partitioner"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by chimerical_brio on 2007-06-30
I resized a Fat32 partition with the GParted LiveCD on a frien'ds computer, leaving an unformatted section of the hard drive ready for Ubuntu. But, when I start up the Ubuntu install process from the Feisty LiveCD, the installation just stops at the partitioning screen ("Prepare disk space"), but after it checks my file system. It just sits there, and nothing happens. I know the disk is fine, I've installed on systems very recently with it. Any ideas? Thanks.

---

### Post by NIT006.5 on 2007-06-30
Does it give you time to change partition settings, or does it freeze before that?

I have not experienced exactly the same issue, but I did have a problem (on several different PC's) where the installation would freeze on 15% (something to do with file systems) and this was solved by removing any and all linux partitions and manually creating the swap and / partitions, as opposed to going with the "default" automatic configuration. But if you don't have a chance to change the partition arrangement before it freezes, then that won't really help. Sorry, no other ideas at this point.

---

### Post by chimerical_brio on 2007-06-30
Well, it just randomly worked, so oh well.Thanks anyway.

---

