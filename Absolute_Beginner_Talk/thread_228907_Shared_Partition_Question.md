---
title: "Shared Partition Question"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by zisme on 2006-08-03
Would it be better to make the shared partition FAT32 or EXT3? I know that Ubuntu and Windows support FAT32, but it doesn't have permissions or support for files over 4GB. I know there is FS-Drive which makes it possible for windows to read+write+more on EXT3 and EXT2.

Thanks for the opinions!

---

### Post by spin2cool on 2006-08-03
I use fat32 with no problems. Of course, I don't deal with 4 GB files, either...

---

### Post by anaconda on 2006-08-03
I use the fs-driver, and havent had any problems with it.
[http://www.fs-driver.org/](http://www.fs-driver.org/)

ext3 is better than fat32 also in that permissions in linux work with ext2/3 but not with fat32. So using ext3 and cliking .txt or .pdf file it won't ask "do you want to execute" the .txt ot .pdf file.. it would just be opened in the right application.. (that is because in fat32 there isnt permissions, and so all files are marked eXecutables, like .exe in windows.. so it asks do you want to execute or open the file ?)

In windows2000 I had problems with bigger than 32GB fat32 partitions (the max size you can make fat32 partition in windows).. sometimes win2000 tries to fix those, and ends up destroying the partition .. To ext3 partitions windows2000 doesn't EVER touch unless asked (using fs-driver.)

---

### Post by zisme on 2006-08-03
Okay! I think I know what I'm going for now. Thanks again!

Zisme

---

