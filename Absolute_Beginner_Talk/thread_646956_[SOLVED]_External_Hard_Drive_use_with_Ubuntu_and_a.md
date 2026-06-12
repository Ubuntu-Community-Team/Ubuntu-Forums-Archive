---
title: "[SOLVED] External Hard Drive use with Ubuntu and a Mac"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by skwon11 on 2007-12-21
Would like to format my new hard drive so that it can be read as well as written to on both my PC (Ubuntu) and my wife's Mac (sorry... she won't switch).  Doesn't need to be networked only plugged in via USB and read/write.  Suggestions?  If formatted with ext3 (I hope I'm writing that correctly) can a mac use the drive?  Thank you.

---

### Post by spiderbatdad on 2007-12-21
dont think mac can access ext2/3

[http://www.macosxhints.com/article.php?story=20040214000632173](http://www.macosxhints.com/article.php?story=20040214000632173)

---

### Post by LaRoza on 2007-12-21
If Mac's can use NTFS use that, otherwise, FAT32.

If Mac's can use EXT3 or EXT2 use that.

I wish I knew more about Macs.

Try: [http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/)

(I know, you'd have found it through the above link)

---

### Post by digga on 2007-12-21
i have a question related to this issue [kinda]

i also have an external hard drive that i used on my windows system. has a few mp3's and photo's on it. i was wondering if i could use this on my new 7.10 ubuntu machine via just plugging it in? and if not, where might i find the command line code to enable it to work? thanks.

---

### Post by blueridgedog on 2007-12-21
If you plug it in, it should mount automatically.  If not, you can be talked through manually mounting it.

---

### Post by Incense on 2007-12-21
Fat32 shouldn't give you too many problems. Everything can read that. I would also look into network attached storage. Then you don't have to worry about file types. 

[http://en.wikipedia.org/wiki/Network-attached_storage]("http://en.wikipedia.org/wiki/Network-attached_storage")

FreeNAS is a good way to go if you have an old computer. 

[http://www.freenas.org/]("http://www.freenas.org/")

---

### Post by ugm6hr on 2007-12-22
> **skwon11 said:**
> Would like to format my new hard drive so that it can be read as well as written to on both my PC (Ubuntu) and my wife's Mac (sorry... she won't switch).  Doesn't need to be networked only plugged in via USB and read/write.  Suggestions?  If formatted with ext3 (I hope I'm writing that correctly) can a mac use the drive?  Thank you.

FAT32 will defintiely work on both with no tweaks.

Only problem is fragmentation (not sure whether Macs can defrag FAT32 - Ubuntu can't as far as I know), and single files can be no larger than 4GB (I think that's right), so you won't be able to create / save DVDs on to the HD.

---

### Post by LaRoza on 2007-12-22
> **ugm6hr said:**
> 
and single files can be no larger than 4GB (I think that's right), so you won't be able to create / save DVDs on to the HD.

4 GB - 1 byte

An annoying limit.

FAT32 isn't the most reliable for file integrity, be sure to back anything up that is essential once and a while, just in case.

---

### Post by blueridgedog on 2007-12-22
> **ugm6hr said:**
> FAT32 will defintiely work on both with no tweaks.

single files can be no larger than 4GB (I think that's right), so you won't be able to create / save DVDs on to the HD.

Wow, I had forgotten about that limit (and I remember when it came out and how much of an improvement over FAT it was).  Wow, how time flies and things change.  In the era of DVD authoring, many computer users keep 4 to 9 gig files commonly.

---

### Post by skwon11 on 2007-12-23
Thanks,

If the max size in Fat32 is 4 gb, then that would be a problem.  Could the drive be partitioned with Fat32 and Ext3?  And if so... can ubuntu do this for me once I purchase the drive?

---

