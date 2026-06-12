---
title: "Defragment a shared FAT32 drive?"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by yeahyeahyeah on 2005-12-04
I have a 10GB FAT32 drive that I'm using to share data on my latop that dual boots ubuntu and XP. I understand that linux really does not require defragmenting, but XP does. Is there any danger in using the XP defragmenter to defragment the partition every once in a while?

Both OSes will be writing to it often.

---

### Post by aysiu on 2005-12-04
[QUOTE=yeahyeahyeah]Is there any danger in using the XP defragmenter to defragment the partition every once in a while?[/QUOTE] I do it all the time, and I haven't seen any adverse effects. If there's a way to defragment it from Ubuntu, I'd love to know.

---

### Post by yeahyeahyeah on 2005-12-04
Cool.

Are there any issues using FAT32? Is it reliable, etc? It's just wierd, using a format from Windows 98.

[QUOTE=aysiu]I do it all the time, and I haven't seen any adverse effects. If there's a way to defragment it from Ubuntu, I'd love to know.[/QUOTE]

---

### Post by aysiu on 2005-12-04
[QUOTE=yeahyeahyeah]
Are there any issues using FAT32? Is it reliable, etc?[/QUOTE] Well, it doesn't have security or permissions (which isn't an issue for me) on files, so anyone can read from/write to them. And it can't hold files bigger than 4 GB large (which isn't an issue for me, since I don't have a DVD burner).

---

### Post by Adrian on 2005-12-04
[QUOTE=yeahyeahyeah]Cool.

Are there any issues using FAT32? Is it reliable, etc? It's just wierd, using a format from Windows 98.[/QUOTE]

Well, first of all, it's not a journaling file system which means that it isn't as reliable as ext3 or NTFS. For more information about journaling file systems, check for instance [http://en.wikipedia.org/wiki/Journaling_filesystem](http://en.wikipedia.org/wiki/Journaling_filesystem).

Besides the problems Aysiu mentioned, I think the issue with internal fragmentation is worth mentioning. I can sum it up by saying that FAT32 wastes a lot of diskspace if you have many small files on a large partition.

(Edit: The rest of the post will be dedicated to explaining this phenomenon technically for those who are interested. Feel free to read if such things interest you)

Basically, the problem is this:
Every file is physically stored in clusters on the disk, and each cluster can contain data from one file only. For large FAT partitions, these clusters become rather big in size. For instance, if every cluster is 32kb, a file that is 1 byte will occupy a cluster of its own, hence using 32kb of the diskspace. Similary, a file that is 33Kb will use two clusters, hence taking up 64kb of the diskspace.
The size of the clusters depend on the size of the partition, so this is no problem for small partitions. However, for partitions larger than 32Gb, it is recommended to use another file system in order to utilize the available diskspace efficiently. Windows XP doesn't even allow you to format FAT32 partitions larger than 32Gb (but that might also be for political reasons... who knows? :) )

Internal fragmentation can't be "defragmented", unlike its "cousin" external fragmentation (which is what we usually refer to as "fragmentation").

(Edit: I tried to make this post a little more suitable for the "Absolute Beginner Talk" section)

---

