---
title: "Linux equivalents to defrag and erase HD?"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by rggavubt on 2007-02-20
In Dapper are there equivalents to Windows defrag and a Windows program that erases/cleans your hard drive?  Are they required?

---

### Post by ed-j on 2007-02-20
Caution: Reply from Novice!

Sadly, no, it appears not, and all of us Total Novices can't sit in front of the Scandisc looking intelligent when we're really dying of boredom. Welcome to Ubuntucheldir, the land beyond the Blue Screen!

I should add: There must be a Format function somewhere? However, I'm not sure if I will ever need it, as the drive seems to tidy itself? You would do well to gather more information on this. All the best!

---

### Post by floke on 2007-02-20
Nope, and nope again.

Linux uses a filesystem known as ext3 (ext2 + a system of journaling), which is extremely resistant to defragmentation.

After every 30 mounts of an ext partition ubuntu will run an fsck on it, which will basically check the disc for errors and for defrags. Don't be alarmed when you boot up your system only to see this occur, its perfectly normal. Also, don't be worried by any results like 2.4% non-contigous files, since this too is perfectly normal. Do some reading on ext3 and journaling to find out more. There's some good threads on this in the forum.

---

### Post by ed-j on 2007-02-20
Many thanks for defraging my 30 mounts question. Bye!

---

### Post by bodhi.zazen on 2007-02-20
Clean/Degunk:

	[http://doc.gwos.org/index.php/RemoveJunkFiles](http://doc.gwos.org/index.php/RemoveJunkFiles)

	[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

	[http://ubuntu-tutorials.blogspot.com/2007/01/cleaning-up-ubuntu-gnulinux-system.html](http://ubuntu-tutorials.blogspot.com/2007/01/cleaning-up-ubuntu-gnulinux-system.html)

---

### Post by rggavubt on 2007-02-20
> **Steve.K said:**
> Nope, and nope again.

Linux uses a filesystem known as ext3 (ext2 + a system of journaling), which is extremely resistant to defragmentation.

After every 30 mounts of an ext partition ubuntu will run an fsck on it, which will basically check the disc for errors and for defrags. Don't be alarmed when you boot up your system only to see this occur, its perfectly normal. Also, don't be worried by any results like 2.4% non-contigous files, since this too is perfectly normal. Do some reading on ext3 and journaling to find out more. There's some good threads on this in the forum.

Thanks for the reply....I love this OS.  All my defraging and erasing days are gone!!

PS...my system hasn't run fsck so far...if it has, I haven't noticed.

---

### Post by floke on 2007-02-21
Oh, you'll see it when it does!:)

---

