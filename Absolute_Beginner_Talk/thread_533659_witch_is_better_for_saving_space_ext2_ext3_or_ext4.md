---
title: "witch is better for saving space ext2 ext3 or ext4"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by cosmoshell on 2007-08-24
witch is better for saving space ext2 ext3 or ext4. I dont care about performance.

---

### Post by amazingtaters on 2007-08-24
What do you mean by saving space? They are just file systems, you have to tell Ubuntu how big to make a partition with any of them on there, and what are you using that supports ext4 already?

---

### Post by Jimmyfj on 2007-08-24
EXT4 is still in development and not yet implemented in Ubuntu. EXT3 is the recommended file system for Ubuntu. Space saving I believe is not a matter of file system but a matter of compression format. I use .ogg for better sound and space saving.

---

### Post by milosz.galazka on 2007-08-24
At default settings 5% of space is reserved for root so system will be working ok if amount of available space will be small.

Don't bother about space saving as filesystem itself will not waste your space. You can also try  google search for reiserfs, xfs,....

---

### Post by Paulmd on 2007-08-24
> **Jimmyfj said:**
> EXT4 is still in development and not yet implemented in Ubuntu. EXT3 is the recommended file system for Ubuntu. Space saving I believe is not a matter of file system but a matter of compression format. I use .ogg for better sound and space saving.

I think the OP is referring to "slack space"

For example, if I create a file of 70 bytes on my computer, it still is allocated 4K. This is a quickie "Hello world" program i created to make sure that gcc worked. It's wasting 4026 bytes (4096 -70) .

```

$ ls -al my*
-rw-r--r-- 1 paul paul 70 2007-08-10 21:18 myproj.c

$ du myproj.c -h
4.0K    myproj.c
```


To answer the OP: it's not really a big consideration unless you have lots and lots of itty bitty files.

---

### Post by milosz.galazka on 2007-08-24
Check manuals for mkfs.ext3 and mkfs.anyotherfilesystem as you can specify block size and other options you probably want.

---

