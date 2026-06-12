---
title: "moving files between linux and windows"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Jimmythestu on 2007-05-06
Silly question but in suse I could move files between windows and linux.  Can you do that in ubuntu?

---

### Post by lluisanunez on 2007-05-06
If your windows files are in a NTFS partition, install ntfs-3g

---

### Post by Happy_Man on 2007-05-06
Sure, from Windows to Linux you need to install ext3 drivers for Windows from [http://fs-driver.org](http://fs-driver.org). For Linux to Windows you need to install ntfs-3g:
```
sudo apt-get install ntfs-3g ntfs-config
```

---

### Post by freebird54 on 2007-05-06
the short answer is yes.  How you do it is a matter of choice for the most part, though some if depends on what your setup is.  (dual boot - networked - VM on one or the other - etc etc.

What would you LIKE to do?  :)

---

### Post by dptxp on 2007-05-06
If running Linux , EXT3 to FAT32 or FAT32 to EXT3 is straight.

Linux does not read NTFS and Windows does not read EXT3. You can however enable both
with some efforts.

---

### Post by quinnten83 on 2007-05-06
> **Happy_Man said:**
> Sure, from Windows to Linux you need to install ext3 drivers for Windows from [http://fs-driver.org](http://fs-driver.org). For Linux to Windows you need to install ntfs-3g:
```
sudo apt-get install ntfs-3g ntfs-config
```

How stable is this? I read somewhere about data getting corrupted, when you try to use this.

---

### Post by freebird54 on 2007-05-06
Not aware of any remaining problems with either (beyond the limitations on software compressed or encrytped files on NTFS).  Seems stable enough.  The other way around is fine too, assuming that the ext3 was shut down properly before being accessed from Win.  If you only do one, however, I would use ext3 for any shared partitions - unless you spend a much larger percentage of your time in Windows...

---

