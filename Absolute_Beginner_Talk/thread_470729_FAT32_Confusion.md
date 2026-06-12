---
title: "FAT32 Confusion"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by LaRoza on 2007-06-11
-edit Problem solved

---

### Post by lazyart on 2007-06-11
FAT32 is limited to 2 gigs?  Since when!?!  I have an 80 gig drive formatted as FAT32.

Maybe you ran out of space on the partition and it couldn't save that second ISO.

---

### Post by LaRoza on 2007-06-11
-edit Solved

---

### Post by Kobalt on 2007-06-11
The maximum possible size for a file on a FAT32 volume is 4 GiB minus 1 Byte.

---

### Post by LaRoza on 2007-06-11
Thanks, I thought the files were the same size, but it was to the byte it seems. Anyway, I was just curious why I could save one and not the other.

I reformatted with a different file system anyway.

---

### Post by ccfjeff on 2007-06-11
> **Kobalt said:**
> The maximum possible size for a file on a FAT32 volume is 4 GiB minus 1 Byte (232&#8722;1 bytes).

According to "The Windows IT Pro" you are right that FAT32 has a 4 Gig size limit:

[www.windowsitpro.com/Article/ArticleID/38803/38803.html]("http://www.windowsitpro.com/Article/ArticleID/38803/38803.html")

---

