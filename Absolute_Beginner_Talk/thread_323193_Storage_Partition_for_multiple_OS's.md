---
title: "Storage Partition for multiple OS's"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by johnnyloot on 2006-12-21
Hi Guys,
So I am currently dual booting XP and Ubuntu (Dapper) on my computer with a 120GB HD.
I currently have it set-up so that XP and Dapper each take up 20 GB so now I have 80GB free.

I would like to use the 80GB as storage for both OS's for say video or music. I remember that from a linux partition you can only read from a windows partition.

What format do I have to make that 80gb position so I can access it from both? EX3? Fat16/32? NTFS?

Thanks

---

### Post by angkor on 2006-12-21
FAT32 will work for both, but I remember I read somewhere that there was software for windows to read  (and maybe write too?) ext3...if this works I'd go for that for stability reasons.

Edit: it's called [explore2fs]("http://www.chrysocome.net/explore2fs") and it seems it only reads ext2 / ext3 but I could be wrong.

---

### Post by Rippey on 2006-12-21
windowsdriver for reading and writing ext2/3
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

---

### Post by Azakus on 2006-12-21
I'd go with FAT32. Both systems can flawlessly read/write to it without any extra steps.

---

### Post by jimrz on 2006-12-21
> **Azakus said:**
> I'd go with FAT32. Both systems can flawlessly read/write to it without any extra steps.

+1 

I have used this setup on quite afew installs various machines and never have had any issues, whatsoever.

---

### Post by scooty on 2006-12-21
Doesn't FAT32 have a file size limit thought? Not good if you're storing DVD images :(

---

### Post by Littleweseth on 2006-12-21
I recommend ext3. the Ext2IFS driver for windows works flawlessly in my experience, and FAT32 is a rather ancient filesystem in many ways - from memory, it's sensitive to fragmentation, can't store unicode filenames, and can't handle files over 4gb. In contrast, ext3 doesn't care very much about fragmentation and the filesize limit is much higher if it exists at all.

The only problems I've had with ext3 occur when linux or windows doesn't get to shut down properly and unmount the filesystem - windows won't mount the drives, and linux runs fsck. (which over my 300gb or so of ext3 partitions takes about half an hour!) I've never lost any data because of this though.

---

