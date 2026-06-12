---
title: "MacHD Permissions"
date: 2009-06-17
forum: Apple Hardware Users
---

### Post by AdamAppleman on 2009-06-17
Ok, so I am currently Dual Booting Windows and OSX on my MacBook Pro and I screwed up my hard drive beyond belief. The good news is, while OSX cannot boot (And the boot disk cannot read its partition) and Windows thinks that my partition is RAW. Linux to the rescue!

In My Ubuntu LiveCD I can view the contents of both my HFS and NTFS drives and the data is still there, unfortunatley I cannot back any of it up because the subfolders in "Macintosh HD" are set with permissions so I cannot view the contents, or back up the data.

My question is this: How can I gain access to these files WITHOUT having the ability to boot into my OSX partition to disable journaling or set privlages?

---

### Post by cyberdork33 on 2009-06-17
open a file browser with root permissions...

"gksudo nautilus"

---

