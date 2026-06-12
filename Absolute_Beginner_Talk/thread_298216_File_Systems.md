---
title: "File Systems"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by guitarist549 on 2006-11-12
While installing a linux distro (I can't remember if it was Ubuntu or not) a while ago, I noticed that there was an option to select different types of file systems, eg. ext2, fat16. I was wonder what the difference between them were because I couldn't find any information about them on the internet.

---

### Post by bodhi.zazen on 2006-11-12
> **guitarist549 said:**
> While installing a linux distro (I can't remember if it was Ubuntu or not) a while ago, I noticed that there was an option to select different types of file systems, eg. ext2, fat16. I was wonder what the difference between them were because I couldn't find any information about them on the internet.

Lots of opinions, few facts. Refine your search.

[Benchmarks](http://linuxgazette.net/102/piszcz.html)

IMO ext3 is conservative, perhaps most secure, and what I am now using. I am interested in jfs and xfs. Concerned with reports of data loss and xfs with power failure.

---

### Post by jaboua on 2006-11-12
Don't use fat16 for your main linux partitions as it's limited by for example not supporting the unix file permissions...

The main alternatives would be EXT3, ReiserFS, XFS and JFS - Ext3 and ReiserFS being the most used ones.

Most of my experience is with ReiserFS. It hasn't let me down the last 2 years, and I read that it's performance should be on par with ext3 regarding big files, however it might be as much as 15 times faster with loads of small files. It also has "dynamic inode creation". An inode is something containing information about files. In e.g. ext3, all inodes will be created at format - thus limiting the number of files, and in addition wasting diskspace if you have few files... In reiserfs inodes are created when they are needed.

Ext3 on the other hand is the true and tried, and said to be the most reliable. Many also speak of a great performance boost if you just tune the filesystem a little bit, can't remember the option's name... It's also probably better if you want safe updates to new versions of the filesystem... Ext4 and reiser4 will probably get into the kernel soon, and while the ext-guys aim for backwards compatibility, reiser4 is an entirely new filesystem that, AFAIK, requires a reformat and atm. is very unstable. There are also many people wondering if reiser4 ever gets into the kernel as Hans Reiser and the kernel developers is in the middle of a fight, and Hans Reiser (the main person in Namesys, the team behind reiserfs) in addition is arrested atm (no evidence, but he is a suspect.. However this is off topic, let's return...)

JFS has only given me corrupt partitions - twice actually... However I doubt that it's JFS' fault, I would rather blame the crappy, old harddrive that I used then...

XFS is said to be good with huge amounts of data, but I don't know all the technical stuff about it...

---

### Post by cotcot on 2006-11-12
When it is all new to you I highly recommend to use ext3.
You can read ext3 from XP using the driver in XP from [www.fs-driver.org](www.fs-driver.org).

---

### Post by ncc74656m on 2006-11-12
AFAIK, the major difference that easily separates types of FS's are journaled and non-journaled. What that comes down to is whether or not they make notes about what they are doing to the HDD before they do it, and thus helping to keep your system running correctly in the event of a crash.

Ext3, ReiserFS, and XFS are the most common examples of journaled systems.

To read some about the different ones, go here: [http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

If you look at it long enough, you can figure it out pretty well... For most new users though, I'd say stay with ext3 for your file storage areas, and ext2 for boot.

---

### Post by moshuptrail on 2006-11-12
What about ext2?  I assume it's a predecessor to ext3.

What would be the pros/cons of using ext2 for an older, maybe under-powered computer?  Is it faster than ext3?  What risks were fixed in ext3?

---

### Post by johnnymac on 2006-11-12
ex2 isn't journaled and ext3 is.  Journaling is a good thing to protect your data if for some reason a disk check is needed.  Journaling gives you the ability to roll forward or back depending on what kind of error occurs on the file system.

---

### Post by ncc74656m on 2006-11-12
Definitely stick with ext3. Ext2 will probably get you into trouble. Once again, not a journaled FS, so any time your system goes down, you could lose data. Think of an old Windows 95 or 3.11 system. But you are right, it predated ext3, but that makes it no better.

And don't think of them as necessarily 'patched' or updated versions of each other. Think of them as different systems entirely, and work with it like that.

---

### Post by bodhi.zazen on 2006-11-12
> **moshuptrail said:**
> What about ext2?  I assume it's a predecessor to ext3.

What would be the pros/cons of using ext2 for an older, maybe under-powered computer?  Is it faster than ext3?  What risks were fixed in ext3?

ext2 is indeed the predecessor to ext3. The disadvantage is that it is not journaled and thus at greater risk for data loss.

ext2 may be faster, regardless of age of hardware and has an advantage of less HD space (for the "journal"). Most people would feel the potential for data loss outweighs the speed or size advantage.

ext2 can be used as /boot (allowing a smaller /boot partition) or on small flash drives. Otherwise I advise a journaled FS.

---

### Post by moshuptrail on 2006-11-12
Thanks for that analysis.  I've been using ext2 for /home.  I think I'll re-think that strategy.

---

