---
title: "how to make external hd talk to OSX and linux?"
date: 2009-07-19
forum: Apple Hardware Users
---

### Post by Mzwo on 2009-07-19
hi,

title says it all, really.

i bought an external harddrive which i intend to use on both laptop (ubuntu 9.04) and imac (OSX 10.5). alas, as i found out, there doesn't seem to be a common file system. NTFS won't work, because it's read only on the mac. ext3 won't work, because it's no-read-at-all on the mac. or so i read.

so, what to do? 

if at all possible, i'd quite like to keep the hd as one single partition.

any hints much appreciated.

cheers,

mzwo

---

### Post by fbugnon on 2009-07-19
I think there is several options to achieve a "bilingual" read-and-write external HD.

**HFS**
From researches I've done long ago, it seems to me that the HFS file system (non journaled, i.e. _not_ HFS**+**) it would be a good option. More info about this on:
```

http://www.tgunkel.de/it/hardware/doc/ibook_g4_linux.en
```

Of course, for the HFS to be readable under Linux, you would need to install _hfstools_ (if I'm not wrong that's the name).

[B]
NTFS[/B]
Could work I guess, just need to install _Fuse_ on your Mac (fuse.sourceforge.net).

**Ext2/Ext3**
I think you could make them read/write from Mac using _ExtFS_, but there are other options.

Further reading: [http://ubuntuforums.org/archive/index.php/t-619909.html](http://ubuntuforums.org/archive/index.php/t-619909.html)

---

### Post by alexmurray on 2009-07-19
I would suggest FAT32 - whilst its not the best filesystem going around (in terms of technical merits etc), it is definitely the most commonly supported one - which is why basically all USB thumb / flash drives use it

---

### Post by Richardcavell on 2009-07-20
I suggest using HFS or FAT32 for the external hard disk.  Ubuntu can read HFS+ but cannot write it. It can read and write HFS. FAT32 is as portable as you can get, but not very UNIX-ish.

Your user and group ids need to be the same under both OS X and Ubuntu.

Richard

---

### Post by Mzwo on 2009-07-20
hi,

thanks for the suggestions. 

am i right in assuming that FAT32 can handle files up to a maximum of 4GB? that may be a problem since i'm mainly working with large audio files.

> **Richardcavell said:**
> 

Your user and group ids need to be the same under both OS X and Ubuntu.

Richard

does this apply to HFS only or any file system?

cheers,
mzwo

---

### Post by Richardcavell on 2009-07-20
In general, FAT32 files are limited to 4 gigabytes. If you want to work with large files, you'll need a workaround or a different file system type.

Your user and group need to be the same on OS X and Ubuntu to access the same files on any file system that recognizes such concepts (such as HFS, HFS+ and ext). FAT32 does not record user and group.

Richard

---

