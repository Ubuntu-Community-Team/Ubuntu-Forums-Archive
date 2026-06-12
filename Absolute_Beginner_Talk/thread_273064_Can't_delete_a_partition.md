---
title: "Can't delete a partition"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by 1002285 on 2006-10-07
I tried to change my partitions -  I had a FAT32 partition for documents (hda5), but I now wanted to have /home on an ext3 partition and now I have the ext3 /home (hda6), and Linux on hda7 as before. But I also want to delete hda5 FAT32 partition and increase the /home partition with the resulting free space. But I got an error sth like "you have to delete partitions with bigger numbers before". And I don't want to delete hda6 and hda7 and hda8.

/dev/hda1   *           1         608     4883728+   7  HPFS/NTFS
/dev/hda2             609        3654    24466995    5  Extended
/dev/hda5            2561        3654     8787555    b  W95 FAT32
/dev/hda6             609        1581     7815559+  83  Linux
/dev/hda7   *        1582        2514     7494291   83  Linux
/dev/hda8            2515        2559      361431   82  Linux swap / Solaris

---

### Post by uk_sphinx on 2006-10-07
you should be able to do that on startup partition.i did.

---

### Post by 1002285 on 2006-10-07
> **uk_sphinx said:**
> you should be able to do that on startup partition.i did.
startup partition?
I'm sorry, I don't understand what you mean. What and where ise this "startup partition"?

---

