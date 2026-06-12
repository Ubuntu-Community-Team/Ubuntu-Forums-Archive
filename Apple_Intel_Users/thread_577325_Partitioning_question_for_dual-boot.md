---
title: "Partitioning question for dual-boot"
date: 2007-10-16
forum: Apple Intel Users
---

### Post by DownloadTHIS on 2007-10-16
If I'm partitioning my hard drive to have one part OS X and one part Ubuntu, is it possible to create a large partition to hold my personal documents and such (music, primarily) that would be accessible from both OSes?

Thanks [=

---

### Post by 505 on 2007-10-16
Yes, just use a partition system that both systems can read anf write, like FAT.

---

### Post by cyberdork33 on 2007-10-16
Note that FAT32 is limited to a maximum 4GB filesize if that is an issue for you.

---

### Post by az on 2007-10-16
There is an ext3 driver for mac OS X.
[http://bmannconsulting.com/macosx/how-to/ext2-for-mac/ext2fsx-readme](http://bmannconsulting.com/macosx/how-to/ext2-for-mac/ext2fsx-readme)

---

### Post by E Gardner on 2007-10-16
I just set up an arrangement like this myself, with a large FAT partition to share files between OSX and Ubuntu.

One issue to watch out for: I used the Gparted live CD to set up the FAT partition, only to find that OS X did not recognize it (disk utility referred to the partition as "microsoft restricted data") and refused to mount, read, or write to it.

I had better luck on my second try, when I set up the FAT partition from OSX's disk utility program, formatting the partition as "MS-DOS". Both systems now recognize the partition and access it without difficulty, and even automatically place an icon for it on the desktop at login.

---

### Post by DownloadTHIS on 2007-10-21
> **cyberdork33 said:**
> Note that FAT32 is limited to a maximum 4GB filesize if that is an issue for you.

4GB is definitely an issue, I've got at least 40GB of music alone. So looks like Ext2 it is.

---

### Post by Tekno_Cowboy on 2007-10-21
I'd go with ext3 not ext2. ext2 has more issues in event of unexpected shutdown.

---

### Post by DownloadTHIS on 2007-10-21
hmm... either way, it looks like that driver doesn't work for 10.4 or 10.5 when that comes out, so I'll need to find another option.

---

### Post by [woodstock] on 2007-10-21
> **DownloadTHIS said:**
> 4GB is definitely an issue, I've got at least 40GB of music alone. So looks like Ext2 it is.

I think that ext is a much better file system than FAT, but I experienced some problems using a file system driver for ext2 for windows. My adventure ended with a totally broken file system (and lost data of course). Hopefully the driver for OSX is more reliable...

cyberdork33 mentioned 4 GB *filesize*, **not** *partition size*! Hence you wouldn't run into problems with a lage music library even if you decide to use FAT as long a a single file isn't bigger than 4 GB.

---

### Post by cyberdork33 on 2007-10-21
if you just have music, I would definitely recommend FAT32. You only need to be concerned about the filesize limitation if you have images of DVD's or something.

---

