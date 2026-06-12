---
title: "disk error problem"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by dhawald3 on 2006-11-28
when booting kubuntu it checks the disk
and it reports 1.6% non contiguous files.

how do I repair it??
Is there any tool for linux file system
like the Norton disk doctor for windows??

---

### Post by bapoumba on 2006-11-28
Hi,
ext3 file system do not fragment (or very little). 1.6% is a good score :) If anything happens to your file system, the automatic checkup performed every 30 mounts will detect it and you will be prompted for a repair. Check **man fsck** for more information.
I've been with ubuntu since warty, and never ever ran into a problem that fsck (or e2fsck) could not solve. I may have been lucky, though :)

---

### Post by steve.horsley on 2006-11-28
My advice is to ignore it. It's not broken, and so doesn't need fixing.

If you really must try and fix it, the best way is to use a live CD to copy everything to another partition (or make a tar file of the partition contents), format the partition, and then restore the backup. At least it's a good test of your backup porocedures.

---

### Post by esaym on 2006-11-28
Non-contiguous doesnt really mean fragmented

Do a search for fragmentation

way too much info for me to just type :wink:

---

