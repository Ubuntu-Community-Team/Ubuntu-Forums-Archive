---
title: "file format for dump drive"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by day1 on 2006-03-25
I was wondering what would be the best file format to use for my drive where I am going to keep my mp3s, video files, etc. (ntfs/fat32)

This is the first time I've actually installed Linux on my personal computer (my university uses it for the introductory programming classes so I've used Linux a little bit). I just want to make sure I do this the right way.

-Thanks

---

### Post by belikralj on 2006-03-25
I'm a newb to Ubuntu my self but most of my friends who have ubuntu dual boot use FAT32 as an intermediate partition that both Windows and Linux dump to. Why I don't know exactly but they told me it is best to only use NTFS with Windows XP..... I know that this isnt the solid answer you were looking for but I think FAT32 would do for mp3's.

---

### Post by belikralj on 2006-03-25
Also NTFS is said to be a more efficient file system, but I know FAT32 works with Ubuntu so I don't need to explore NTFS possibilities as of yet.

---

### Post by day1 on 2006-03-25
Ok I thought I would go with fat32, thanks for the response.

---

### Post by trent dillman on 2006-03-25
ntfs support in linux isn't quite 100%, and you risk file/disk corruption.

fat32 has its own limits (filesize of 2g), but is supported better

---

