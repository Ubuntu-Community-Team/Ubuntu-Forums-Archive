---
title: "Make windows observe linux permissions?"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by thesm on 2006-05-08
I have one windows partition (ntfs) and the rest are ext2, but the ext2 driver to make the partitions usable in windows doesn't preserve permissions.  I'm wondering if a FAT permission in windows will preserve the permissions.

thesm

---

### Post by mcduck on 2006-05-08
[QUOTE=thesm]I have one windows partition (ntfs) and the rest are ext2, but the ext2 driver to make the partitions usable in windows doesn't preserve permissions.  I'm wondering if a FAT permission in windows will preserve the permissions.

thesm[/QUOTE]
NTFS and FAT filesystems aren't able to store linux file attributes. As soon as you move/copy the files to win filesystem, they loose their permissions. There's no way around it.

But if you make a tar.gz, the files inside it will keep their permissions when you move the file around..

---

### Post by Omnios on 2006-05-08
I have a Vfat-32 partition and it fakes permitions rather well. I use it as My      Documents drive and to back up my Linux Files when installing new releases.

---

