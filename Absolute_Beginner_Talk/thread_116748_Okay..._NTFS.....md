---
title: "Okay... NTFS...."
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by JoeZ on 2006-01-13
Please... I have read so much but I still cant get it to work...
Can someone tell step by step of how you do?
read and copy in a NTFS partion?

---

### Post by aysiu on 2006-01-13
See the fourth link of my sig. It's step by step as long as you know where the terminal is (Applications > Accessories > Terminal) and know how to copy and paste commands.

---

### Post by towsonu2003 on 2006-01-13
[QUOTE=JoeZ]
read and copy in a NTFS partion?[/QUOTE]
linux doesn't support writing (copying files, changing their names etc) to ntfs (ok it does but it's experimental > which means you may corrupt your filesystem writing to a ntfs from linux) so be careful :) reading (seeing files, copying them to linux etc) is fine.

---

### Post by hillbilly on 2006-01-13
The best thing that you could do is mount your windows partition from linux so that you can read windows(nfts) data in linux.
Additionally you can create a FAT32 partition which can be accessed by both linux and windows. This will enable you to add/modify/delete data from this partition using either linux and windows.

---

