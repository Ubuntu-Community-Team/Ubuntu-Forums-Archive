---
title: "File Storage Partition File System"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by andrew_f on 2007-09-05
I really like Xubuntu. I haven't been on my Windows XP OS in a week or so. If (crosses fingers) I can get all my needed hardware/software to work under Linux, I think that I can finally ditch Windows once and for all. I will format the ~30gb 'NTFS' partition that it currently sits on and then use it as a dedicated file storage partition, separate from Xubuntu's own smaller partition (just for better organization and so it's not affected if the OS should ever die and I need to format it's partition).

My question is, which file system should I format the "new" partition into to obtain the best results and ease of access (no read/write issues) from Xubuntu? I'm assuming 'FAT32' but I'm not positive.

Thanks.

---

### Post by jerutley on 2007-09-05
Which filesystem to use is highly subjective - it depends on the type of data you'll be storing there, and how irreplaceable that data is.  If your machine is going to be Linux-Only after you do this, then I would *NOT* go FAT32 - the only real reason to use a FAT32 partition is to have write access by both Windows and Linux in a dual-boot situation.  Myself, I would use ext3, ReiserFS3, or XFS, depending on the type of data you're storing.  Ext3 is the most stable, but doesn't have the performance of the other 2 in most cases.  Reiser3 is the best when you have a LOT of small files, while XFS is better when your files are larger (storing ISO's for example, or large movies).

---

### Post by andrew_f on 2007-09-05
Thank you for that chunk of information, it was very helpful. Based on my situation and your info. I have decided that I will use the ext3 file system.

---

### Post by hyper_ch on 2007-09-05
General rule: If you are unsuare what linux file system to use, then you have to use ext3 ;)

---

