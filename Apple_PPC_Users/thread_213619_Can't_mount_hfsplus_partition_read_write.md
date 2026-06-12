---
title: "Can't mount hfsplus partition read write?"
date: 2006-07-11
forum: Apple PPC Users
---

### Post by Rob_Frohne on 2006-07-11
Hi All,

After installing Dapper, I can't seem to mount my hfsplus partition read write.  Under Breezy it worked fine.  The mount command indicates it is r/w, but when I touch a file there, it says that the drive is a read only filesystem.  Does anyone have any ideas?

Thanks,

Rob

---

### Post by pindar on 2006-07-12
Newer kernels don't let you write to a journaled hfs+ filesystem because it could produce inconsistencies. If you want write access, disable journaling on your partition. From within OS X, in a terminal window:

```
sudo diskutil disableJournal diskXsX
```

where X is the number of your disk and your partition.

---

### Post by bunny64 on 2006-10-26
Merf~!!

This broke my iMac, it will no longer boot and I can't disable journalling in install disc disk utility ;---;

Halp?

---

