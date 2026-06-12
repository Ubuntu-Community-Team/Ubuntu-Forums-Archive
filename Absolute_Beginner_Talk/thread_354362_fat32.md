---
title: "fat32"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by antgul3382 on 2007-02-05
ok on my machine i have windows xp mce on one partition ubuntu on another two and a fat32 partition for all my stuff. i move files around alot and i was wondering if in linux theres a "defragment" tool??

---

### Post by spin2cool on 2007-02-05
I spent a while looking around for this in the past and found the following info.  On ext filesystem drives, there's no need to defrag.  If you're dual booting with a FAT32 drive, though, you have two options

1) Boot back into windows and defrag using the MS utilities.
2) copy everything off of the old partition onto a new one, delete the old data, then copy everything back to the old partition

---

### Post by antgul3382 on 2007-02-06
well that sucks.....so under ubuntu nothing gets fragmented??? what if i just ran ubuntu and no windows???

---

### Post by pay on 2007-02-06
Linux doesn't really need them. If you ran just Ubuntu, you would probably be using the EXT3 file system.> Q:
When I was using Windows, I had to run a defragmentation program quite often to speed up my computer. Where do I do this in Linux?

A:
Unlike Windows' filesystems, most filesystems that run on Linux have no need of being defragemented because they prevent fragments from occurring in the first place.

If you use the default filesystem (ReiserFS), you'll never have to defragment your hard drive as long as you use it.Information found [here.](http://www.novell.com/coolsolutions/qna/15032.html)

[This](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting) link will explain it all.

---

