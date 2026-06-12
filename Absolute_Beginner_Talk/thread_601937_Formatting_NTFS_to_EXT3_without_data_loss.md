---
title: "Formatting NTFS to EXT3 without data loss"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by Kin'iroi Tatsu on 2007-11-03
I have a slight dilemma.  I would like to reformat two of my ntfs partitions that formerly contained Windows to ext3, so that I can have proper permissions on the files on the drive, but I don't have any method to backup the files, and I have very little free space left. Is there a way to change an ntfs to ext without reformatting in the same fashion that M$ can convert fat32 to ntfs?

---

### Post by Dr Small on 2007-11-03
When you format something from one format to another, it does it's job, and **reformats** the drive, essentially erasing everything on it.

---

### Post by Ink-Jet on 2007-11-03
Why bother?
Ubuntu can read/write NTFS drives.

---

### Post by Kin'iroi Tatsu on 2007-11-03
the problem is not reading or writing files, I need to be able to access files through my apache server and you cannot access ntfs drives from apache because others does not have r+w permissions, is there a way around that other than reformatting maybe?

---

### Post by carlosjuero on 2007-11-03
the only possible way is to backup to CD (if possible) or to migrate the data onto ext3 partitions temporarily. ext3 is too much of a different structure than NTFS to migrate properly, unlike migrating from FAT32 to NTFS (both FAT32 and NTFS share certain qualities [naming conventions, etc]).

If you can find a way to take your data and put them onto your existing ext3 partitions, then you can do it that way - or if you can merge the data on the NTFS partitions (by copying) [or even a combo of both - use the free space on the drives smartly], and then format one at a time.

Otherwise, you can look into putting some onto an online backup service (or a free storage service, whatever is available to you) then that can help.

---

### Post by Kin'iroi Tatsu on 2007-11-03
Thanks, I backed up the files to DVD, and converted the partitions.  Good suggestion.

---

