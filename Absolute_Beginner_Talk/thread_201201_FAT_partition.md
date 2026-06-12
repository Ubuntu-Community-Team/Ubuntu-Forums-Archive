---
title: "FAT partition"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by skale on 2006-06-21
Is it possible to keep an ext3 partition just for the operating system and run windows and all the files on a FAT32? How large should the ext3 partition be?
Would there be any issues?

---

### Post by Tedd on 2006-06-21
Question's a little hard to understand. Do you mean dual-booting (using Windows and Linux on the same computer)?

If so, yeah. I personally use NTFS, but whatever floats your boat.

---

### Post by Kilz on 2006-06-21
[QUOTE=skale]Is it possible to keep an ext3 partition just for the operating system and run windows and all the files on a FAT32? How large should the ext3 partition be?
Would there be any issues?[/QUOTE]
The Fat32 partition for windows is a good choice if you want Linux to be able to read and write to the files on that partition. As For what size the ext3 partition should be, the release notes say a minimum of 3 gigabytes. If you can spare 6-10 that would be better.

---

### Post by steve.horsley on 2006-06-21
Your home folder needs to be on a proper filesystem. Best is to put a symlink in your home folder that links to the FAT partition mount point.

---

