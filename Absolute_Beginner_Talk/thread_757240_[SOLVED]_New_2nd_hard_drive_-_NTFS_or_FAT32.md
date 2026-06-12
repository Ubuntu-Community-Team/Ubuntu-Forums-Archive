---
title: "[SOLVED] New 2nd hard drive - NTFS or FAT32?"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by cifdtruckie on 2008-04-16
I'm installing a 2nd hard drive on which to dump mp3's and torrents.  I'd like to be able to read/write from both XP and Ubuntu.  Should I partition as NTFS or FAT32?

---

### Post by Tom--d on 2008-04-16
Fat32 as it works on both OS :)

---

### Post by cifdtruckie on 2008-04-16
Awesomeness - thanks!

Anything else I should know before proceeding to partition?

---

### Post by Tom--d on 2008-04-16
NTFS = NT File system ;)

Thats all I know xD

---

### Post by FuturePilot on 2008-04-16
I'd go with NTFS. FAT32 is old and has a lot of limitations. If you have any files over 4GB you won't be able to put those on FAT32. FAT32 also has a small partition size limit to it. NTFS support under Linux has greatly improved and is supported out of the box on Gutsy.

---

### Post by cifdtruckie on 2008-04-16
Good to know!  Thanks!

---

### Post by Tom--d on 2008-04-16
> **FuturePilot said:**
> I'd go with NTFS. FAT32 is old and has a lot of limitations. If you have any files over 4GB you won't be able to put those on FAT32. FAT32 also has a small partition size limit to it. NTFS support under Linux has greatly improved and is supported out of the box on Gutsy.

NTFS never worked out of the box for me.. took quite a while to mount my external hard drive. 

What else formats are there which work with all os's?

---

### Post by benrboone on 2008-04-16
I would go with ntfs as is better for big files (especially those over 4gb)
Ubuntu has good read write support for ntfs for a while now.
You may also use ext3 as there are drivers for windows available

---

### Post by PeterJS on 2008-04-16
I've torented a bunch of stuff to my ntfs partition and never had any problem with it. FAT32 will work with both OSes but won't work well with either (4gb file cap, etc). NTFS is as good as it gets under windows, and ntfs-3g under linux is just fine, especially if you get the netfs-config tool to set it up for you.

---

### Post by skyhook19 on 2008-04-16
NTFS is the way to go.  I've never had any problems with it at all in ubuntu.

---

