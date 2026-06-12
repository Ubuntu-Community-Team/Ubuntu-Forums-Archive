---
title: "Ubuntu won't read NTFS drive"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by Shack_ on 2007-02-26
I'm trying to get Ubuntu to read an external USB hard drive. It is formatted in NTFS. I thought that while Ubuntu could read NTFS, it couldn't write to it. But for some reason, when I open the contents of the drive, it says there are two folders, "$RECYCLE.BIN", and "System Volume Information". On Windows however, the drive is completely blank. I tried placing files on it from Windows, but in Ubuntu the files wouldn't show up.

Why can't Ubuntu read it, and how do I fix it?

---

### Post by NT4usB on 2007-02-26
> **Shack_ said:**
> I'm trying to get Ubuntu to read an external USB hard drive. It is formatted in NTFS. I thought that while Ubuntu could read NTFS, it couldn't write to it. But for some reason, when I open the contents of the drive, it says there are two folders, "$RECYCLE.BIN", and "System Volume Information". On Windows however, the drive is completely blank. 
Those files are 'hidden' by default in windows. 
Linux don't care. 
You'll find deleted files you thought were gone, in $RECYCLE.BIN. You can even save them to, and open them in Linux, and copy them back to your PC.

> **Shack_ said:**
> I tried placing files on it from Windows, but in Ubuntu the files wouldn't show up.

Why can't Ubuntu read it, and how do I fix it?
I dunno. I have a half dozen NTFS USB drives and Ubuntu reads them all...

---

