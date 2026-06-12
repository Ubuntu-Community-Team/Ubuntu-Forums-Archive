---
title: "[SOLVED] Vista read ext3 volumes?"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by keymoo on 2007-08-16
Hi there,

My laptop is currently dual booted with Vista Enterprise. I was thinking of installing [this]("http://www.fs-driver.org/index.html"), does anyone know of any problems running this software in Vista? Is there any other software I should consider for the same task?

Thanks

---

### Post by gn2 on 2007-08-16
You could also consider having an NTFS shared data partition and using ntfs-3g with Ubuntu.

---

### Post by frodon on 2007-08-16
> **gn2 said:**
> You could also consider having an NTFS shared data partition and using ntfs-3g with Ubuntu.Yes but it is far better to know which OS you use the most, choose NTFS if you use more windows and ext3 if you use linux first.
If you think you will use one as much as the other then concider to have a big FAT32 partition because FAT32 have full support in both OS however FAT32 can't write file bigger than 4Gb.

---

### Post by DaZjorz on 2008-04-09
Please have [SOLVED] removed from the title, since the two replies were **not** answers to the question! (The question was "how to read ext3 partitions from Windows Vista", the answer was "how to read/write to ntfs partitions from Linux")

I've used [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html) before, but not on Vista, but going to try now. :)

---

