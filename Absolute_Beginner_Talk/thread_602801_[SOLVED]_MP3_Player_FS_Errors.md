---
title: "[SOLVED] MP3 Player FS Errors"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by bobbocanfly on 2007-11-04
I have a Sansa e280 running Rockbox, which for some stupid reason i unplugged without ejecting proerly and got some filesystem damage. All my files went away, except for a couple (just enough to let me boot).

I ran FSCK on it but i sdont know what to do now:

> bobbo@penguin:~$ fsck /dev/sdc1
fsck 1.40.2 (12-Jul-2007)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  71:53/4e, 72:61/4f, 73:6e/20, 74:73/4e, 75:61/41, 76:20/4d, 77:65/45
  , 78:32/20, 79:38/20, 80:30/20
1) Copy original to backup
2) Copy backup to original
3) No action
? 



---

### Post by bobbocanfly on 2007-11-04
I somehow managed to fix it.

I selected option 3, Ctrl+C'd out of it, cd into the mount point then sudo rmed *.rec and its working perfectly now.

---

