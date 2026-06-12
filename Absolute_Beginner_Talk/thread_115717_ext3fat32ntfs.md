---
title: "ext3/fat32/ntfs?"
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by tiggs_the_cat on 2006-01-11
Hello there,

I'm thinking about setting up a dual-boot with Ubuntu on one hard drive, WinXP on the other, and having another drive for storing my files. I read that ext3 is the default file system for Ubuntu.

What file systems could I use so that both Windows and Linux can read and write files from/to the storage drive? I guess NTFS won't work but what about ext3? I didn't find any information if WinXP can read and write to ext3. If not, should I use Fat32 for that drive?

Also I read that there are no defragmenting tools for ext3. What do you do when your hard drive gets fragmented?

:) Thanks alot!

---

### Post by frodon on 2006-01-11
You can get read support for ext3 under windows thanks to [ext2ifs]("http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm") drivers or [those]("http://www.osnews.com/story.php?news_id=11506") drivers.

You will have no problem to use read/write on FAT32 with both OS that's why it's a good solution for users who use both windows and linux, however you have to know that FAT32 don't support unix rights and ownership.

Here is a good dual boot install guide for ubuntu : [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Cyhatch on 2006-01-11
Yes, NTFS is not suitable for this (at least it wasn't ~1 year ago, heh).

For the Windows-extX question, please see the [Ubuntu Starter Guide]("http://www.ubuntuguide.org/#readlinuxpartitionsinwindows").

On defragmenting ext3: you can see what [Wikipedia]("http://en.wikipedia.org/wiki/Ext3#Disadvantages"), for example, says about it; or just search [Google]("http://www.google.com/search?q=ext3+defragment&sourceid=mozilla-search&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox&rls=org.mozilla:en-US:unofficial"). But you wouldn't probably need to defragment at all: for example, my heavily-used 20 Gb /home patition is 60% full and about 5% fragmented.

---

### Post by Alpha_toxic on 2006-01-11
I suggest trying this [http://www.fs-driver.org/](http://www.fs-driver.org/)
This little thingy provides full read/write access from a win NT4.0/2000/XP to ext2/ext3 partitions. It actually uses ext3 only as a ext2, but this is not a problem, as older linux kernels did the same thing (ext3 is the same as ext2, the only difference is the journal). The best thing is that this is done at system level, so all your programs should work on the ext3 partition.
Note: I haven't tryed it my self (I'm dualbooting with 2003, wich is not supported by the driver), but a friend of mine tried it and it works just fine.

Using the driver you can use an ext3 partition for r/w access from both win and linux, wich is much better than keeping a FAT32.

As for the fragmentation - this was one of my first questions on this forum too :) . It seems that fragmenting an ext3 is sth very very hard to do and I'm perfectly happy with it :)

---

### Post by frodon on 2006-01-11
Be careful !

Don't use the write support of any ext2/3 windows drivers, it works but it's no reliable. If you use write support really often you could corrupt your ext2/3 partition.
However no problem with read support.

Summary of available ext2/3 drivers for windows :
[http://www.fs-driver.org/](http://www.fs-driver.org/)
[http://www.osnews.com/story.php?news_id=11506](http://www.osnews.com/story.php?news_id=11506)
[http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm)

---

### Post by tiggs_the_cat on 2006-01-11
frodon, Cyhatch and Alpha_toxic,

Thank you all very much for your fast and very helpful replies, I'll definitley check out all of your links and advice! Very much appreciated! :D

[Edit]frodon, thank you very much again for the warning, I will keep it in mind! :D

---

### Post by Alpha_toxic on 2006-01-11
frdon are you sure that the write support can be harmfull? I really hoped that I can finaly get rid of my FAT32 partition, but if that thing can break, I'll pass (I can not get rid of win either, I have to be compatible with the soft at my university :( ).

---

### Post by frodon on 2006-01-11
Yes it can, most of users don't get this kind of problems but there's still a risk and that's why i often advice to keep a small FAT32 partition, but i really hope that will change soon.

I think lot of users will tell you that they never get any problems using the ext2ifs drivers but even if the risk is small the risk is :(.

So i think the best solution is to make good partitioning, for example if you have a 300Go disk i would use 250Go as ext3 and 50Go as FAT32.

**Alpha_toxic,** why not create a poll thread where users will give you their feedback about ext2/3 drivers, it might be the best answer to your question.

---

### Post by Thirsteh on 2006-01-11
FAT32 will work sweetly.

---

### Post by frodon on 2006-01-11
Yes but it doesn't support unix rights and ownership which is really annoying and less secure.

---

