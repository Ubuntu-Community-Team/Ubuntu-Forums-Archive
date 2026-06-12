---
title: "extrecting .bz2 has error"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by iatebe on 2007-12-29
i download pidign's source from its homepage. Then i use 'tar -xjvf pidgin-2.3.1.tar.bz2' to extract but procceses have lots of errors :(, like this :

```
pidgin-2.3.1/finch/libgnt/gntbox.h
tar: pidgin-2.3.1/finch/libgnt/gntbox.h: Cannot utime: Operation not permitted
pidgin-2.3.1/finch/libgnt/gntlabel.h
tar: pidgin-2.3.1/finch/libgnt/gntlabel.h: Cannot utime: Operation not permitted
pidgin-2.3.1/finch/libgnt/gnt.h
tar: pidgin-2.3.1/finch/libgnt/gnt.h: Cannot utime: Operation not permitted
pidgin-2.3.1/finch/libgnt/gntcolors.h
tar: pidgin-2.3.1/finch/libgnt/gntcolors.h: Cannot utime: Operation not permitted
pidgin-2.3.1/finch/libgnt/gntmenuitem.c
tar: pidgin-2.3.1/finch/libgnt/gntmenuitem.c: Cannot utime: Operation not permitted
pidgin-2.3.1/finch/libgnt/gntclipboard.c
tar: pidgin-2.3.1/finch/libgnt/gntclipboard.c: Cannot utime: Operation not permitted
pidgin-2.3.1/finch/libgnt/gnttextview.c
tar: pidgin-2.3.1/finch/libgnt/gnttextview.c: Cannot utime: Operation not permitted
pidgin-2.3.1/finch/libgnt/gntkeys.c
tar: pidgin-2.3.1/finch/libgnt/gntkeys.c: Cannot utime: Operation not permitted
pidgin-2.3.1/finch/libgnt/gntcheckbox.h
tar: pidgin-2.3.1/finch/libgnt/gntcheckbox.h: Cannot utime: Operation not permitted

```

so, can u help me to solve this problem, plzzz ?? :(

---

### Post by blueridgedog on 2007-12-29
Try unzipping it first before untaring it:

bunzip2 pidgin-2.3.1.tar.bz2

Then

tar xvf pidgin-2.3.1.tar

---

### Post by Bachstelze on 2007-12-29
You're trying to extract it on a FAT32 or NTFS filesystem, right? Those filesystems don't support UNIX timestamps, thus the warnings. Compilation should work fine nevertheless but you should extarct the source on a Linux filesystem instead.

---

### Post by iatebe on 2007-12-29
> **HymnToLife said:**
> You're trying to extract it on a FAT32 or NTFS filesystem, right? Those filesystems don't support UNIX timestamps, thus the warnings. Compilation should work fine nevertheless but you should extarct the source on a Linux filesystem instead.

right, ur right :) i understand now, thank u all for responding :)

---

