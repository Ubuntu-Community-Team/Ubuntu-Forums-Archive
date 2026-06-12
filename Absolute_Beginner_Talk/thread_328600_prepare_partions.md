---
title: "prepare partions"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by xxhopingtearsxx on 2006-12-31
how do i do that?
[http://img155.imageshack.us/img155/3233/w2u302wy.png](http://img155.imageshack.us/img155/3233/w2u302wy.png)
thats where im at.
what do i do
so my linux can have 17 gb
and my xp has 35.58 gb - 17 gb (whatever's left) (Something in the 30s gb or 20s gb)
PLEASE

(PS: that screenshot is not a screenshot of mines)

---

### Post by xxhopingtearsxx on 2006-12-31
bump

---

### Post by bruenig on 2006-12-31
I am confused, what does your partition table look like, you said the one in the screenshot isn't yours?

---

### Post by xxhopingtearsxx on 2006-12-31
forget that, sorry.
um
in [http://img153.imageshack.us/img153/2556/w2u310xn.png](http://img153.imageshack.us/img153/2556/w2u310xn.png)
i got this error (thats not a screenshot of my error, i cant take screenshots since my livecd doesnt have internet. im on my twin's comp.)

"FAT and NTFS filesystems may not be used on filesystems used by the system (/,boot,/home./usr,/var, etc.) it is usally best to mount them somewhere under (/media/.)

---

### Post by xxhopingtearsxx on 2006-12-31
bump

---

### Post by Sef on 2006-12-31
> "FAT and NTFS filesystems may not be used on filesystems used by the system (/,boot,/home./usr,/var, etc.) it is usally best to mount them somewhere under (/media/.)

For Ubuntu, you should use the default file system: ext3.   NTFS only works with Windows.  FAT32 is only for sharing files between Linux and Windows; however, you can do that with ext2 or ext3 as well.

---

### Post by xxhopingtearsxx on 2006-12-31
how do i use the ext3?

---

### Post by Sef on 2006-12-31
> how do i use the ext3?

If you are using the Live CD or alternate cd, it is the default file system, so you don't have to change it at all.   For swap, you would set the file system to swap.  

If you are partitioning before installing, use [GParted]("http://gparted.sourceforge.net").  It is gui partitioner, so easy to use.

Do **not** use Partition Magic as it and Linux tend not to get along well.

---

### Post by xxhopingtearsxx on 2006-12-31
well, i gave up installing it, i'll try again today, and just follow instructions easily.

but i keep getting a message saying my (D) drive (the one i use to do system recovery) is low on disk space.

---

