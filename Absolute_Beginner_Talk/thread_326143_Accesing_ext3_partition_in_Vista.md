---
title: "Accesing ext3 partition in Vista"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by milad on 2006-12-27
I have both Ubuntu and Windows Vista installed (dual boot) and I'm wondering if there is any way that i can access my ext3 partition in windows. I saw a program [here]("http://fs-driver.org/") which enables ext2 access in XP. Does anoybody know something like this for ext3 partitions and windows vista?

---

### Post by milad on 2006-12-27
I found something [here]("http://www.chrysocome.net/explore2fs") but it seems to be only an explorer. what I need is a program which enables windows to work with ext3 partitions just like other ones, such as ntfs or fat32. The program I mentioned in the first post seems to do that. but it doesn't support ext3 and vista :(

---

### Post by bmt on 2006-12-27
As far as I know, ext3 is the same as ext2, but with journalling added.  An ext3 partition can be read and written as ext2.  So that's not something to be worried about.

The [ext2fsd page]("http://sourceforge.net/projects/ext2fsd") says that it works with Vista.  I have no experience of using it.

---

### Post by Skardal on 2007-01-16
I've tried both [fs-driver]("http://fs-driver.org") and [ext2fsd]("http://sourceforge.net/projects/ext2fsd"), both without success.

I really hope someone figures out a solution! I have everything of my media files on my linuxpartitions :-?

---

