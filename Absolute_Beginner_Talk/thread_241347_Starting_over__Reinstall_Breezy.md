---
title: "Starting over:  Reinstall Breezy?"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by brn on 2006-08-22
I have a 2nd hand Dell Latitude CPx laptop (256 RAM/650 MHz/20 GB) that came with Windows XP installed.  Installing Breezy I repartitioned the disk like this:
        6 GB  ---  ntfs    --- Windows
        4 GB  ---  FAT32   --- Common Linux/Windows 
        4 GB  ---  Ext3    --- Linux (/)
        4 GB  ---  Ext3    --- Linux (/usr)
        1 GB  ---  Ext3    --- Linux (/home)
      512 MB  ---  Ext3    --- linux (swap)
      512 MB  ---  FAT32   --- DOS
This was my best guess as to what kind of space I should allocate for which components.  I know better now.  When Dapper arrived I presumed that I could install it and repartition like this;
        6 GB  ---  ntfs    --- Windows
        4 GB  ---  FAT32   --- Common Linux/Windows
        8 GB  ---  Ext3    --- Linux (/)
        1 GB  ---  Ext3    --- Linux (/home)
      512 MB  ---  Ext3    --- Linux (swap)
      512 MB  ---  FAT32   --- DOS
To my chagrin the Dapper installation partitioner (gpartd?) didn't work at all like that with Breezy.  I stepped gingerly through the procedure and came out with the same partitions I started with (and wanted to change) except that they were not recognized by name.  Dapper identified them as hda1 thru hda8 and put everything in the now overloaded hda3. Now these partitions sit on my Gnome desktop as useless glyphs that I cannot delete. I know I must have missed something but right now I'm thinking of re-installing Breezy (for the more tractable partition menu) and trying to start from scratch.  Any advice will be appreciated before I goof up again.

THanks!

---

