---
title: "External HD - file system?"
date: 2012-01-20
forum: Apple Hardware Users
---

### Post by canhoto on 2012-01-20
If I want to use the same external HD to backup my Mac and my Ubuntu files, what should I do?

- Use the same partition? Which file system should I use?
- Have two separate partitions? With which file systems?

---

### Post by deonis on 2012-01-20
not sure we can read any eh* file systems on Mac, so, I would say that the best choice would be two partitions. One with XFS and another with ext3-ext4, your choice ...

---

### Post by bcschmerker on 2012-01-20
[Apple Computer, Inc.](http://www.apple.com/), developed a Hierarchical File System (HFS) for MacOS®; HFS Plus has been used since MacOS® 8.0.  Handling HFS Plus in recent versions of LinUX (Kernels 2.6 and 3.x) requires specific Apple Macintosh file system and Extended HFS file system support at the kernel level; further information is at the [Gentoo® LinUX Wiki](http://en.gentoo-wiki.com/wiki/Hfsplus).

---

### Post by Q-collective on 2012-01-22
Mind that you need HFS+ *journaled* (also known as "Mac OS Extended (Journaled)") to let Time Machine work properly. HFS+ is just the *extended* version of HFS.

---

### Post by canhoto on 2012-01-22
Ok, as I read that the problem is *journaling* I just created two partitions:

- One HFS+, for my Ubuntu backups
- One HFS+ journaled, for my Mac Time Machine backups.

And it's working.

Thanks!

---

