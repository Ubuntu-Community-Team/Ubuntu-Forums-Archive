---
title: "Is it OK to use RieserFS instead of ext3?"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Xuratoth on 2007-05-12
I had to select ReiserFS instead of ext3 during the installation of Feisty as each time I selected ext3 the installer failed after about 10% telling me it could not create the partition. I have reported this as a bug (its possibly due to the old partition being an OS/2 HPFS partition, at a guess).

My question is: Was selecting RieserFS OK, will it cause me problems later on as it is not the default Ubuntu selection, and if so, should I reinstall now over my fresh Ubuntu install now that the HPFS partition is gone, and before I start customising my installation too far?

Many thanks.

---

### Post by Najand on 2007-05-12
Reiser File System is OK. There is no problem using that. In fact it is much faster than EXT3. That is why it is usually used for RAID Systems.

---

### Post by jrusso2 on 2007-05-12
I have had no problems with Reiser but I am sure there will soon be some posters with their horror stories.

Most linux people seem to favor ext 3 because it was developed from the original ext 2 linux file system.

So Reister. XFS, JFS all suffer from NIH.

"not invented here"

---

### Post by Cypher on 2007-05-12
ReiserFS is as good a choice as EXT3, but I think the real answer relies on what kind of function your system will perform. There have been benchmarks performed on EXT3, ReiserFS and a few others and clear indications of where one FS excels at a certain application.

Either way, you will not have any problem because you chose to go with ReiserFS as opposed to EXT3.

---

### Post by steve.horsley on 2007-05-12
Reiserfs is fine. I've used it for a long time, because it was the default FS for SUSE which was the first recent Linux I tried. I am currently using JFS - I thought I'd give it a spin after reading SCO's glowing descriptions of it and how it had transformed Linux into an enterprise system. I can't say I've noticed any difference personally, but anything that would tick SCO off is fine by me.

---

### Post by Xuratoth on 2007-05-12
Many thanks for the answers. 

It's just for a desktop general-purpose system (Web, Mail, some development, small-scale MySQL), so nothing too taxing - sounds like it doesn't matter which file system I use then.

---

### Post by Enverex on 2007-05-12
> **Najand said:**
> Reiser File System is OK. There is no problem using that. In fact it is much faster than EXT3. That is why it is usually used for RAID Systems.

That's just not true. Other than stating the obvious that if it was that everyone would be using it over ext3 anyway. It performs faster when working with thousands of tiny files at once (for example Gentoo's portage ebuilds) but other than that it's aging now and isn't upgrable (easily or properly anyway) where as using EXT3 will allow you to switch to ext4 in future.

---

### Post by energiya on 2007-05-12
It seems to me that EXT3 is loosing ground ... ReiserFS or XFS are way faster and still stable.

---

### Post by cotcot on 2007-05-12
It is maybe not a discussion of which is the best. More, what do you want. Ext3 is OK. If you want to change the partition size when you in the partition then reiser is a possibility. The future reiser is reiser4. 
Check the features and take the one that fits your requests best. Other ext3 is fine.

---

