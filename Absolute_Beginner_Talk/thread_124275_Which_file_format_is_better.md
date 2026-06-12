---
title: "Which file format is better?"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by Leo_01 on 2006-02-01
I am currently reading up on guides to install Ubuntu on computers with Windows... (dual booting)
Which file format is better? EXT3 or FAT32 ? (the guide i used suggests using FAT32... Does ubuntu even run on FAT32?) (Does Win XP read EXT3 file format?)

---

### Post by Perfect Storm on 2006-02-01
I'll recoomend that you use EXT3 for your ubuntu and FAT32 for your windows. But I'm sure that someone with more knowledge on that subject can give you a deeper explaination.

---

### Post by gravediggers on 2006-02-01
XP won't read ext3 filesystem but as AI pointed out, this is better than fat32 for linux. If you have both OS on the same pc, then I suggest you have a fat32 partition to share any files between them. If you have XP on one box and linux on another, then just use NTFS ( or fat32) for XP, and ext3 for linux. You can then setup samba to share files.

---

### Post by frodon on 2006-02-01
[QUOTE=gravediggers]XP won't read ext3 filesystem[/QUOTE]
Really ! : 
[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)
[http://www.fs-driver.org/](http://www.fs-driver.org/)
[http://digg.com/linux_unix/ext2_3_indexed_file_system_read_write_support_for_windows](http://digg.com/linux_unix/ext2_3_indexed_file_system_read_write_support_for_windows)

I advice you to **NEVER** use NTFS if you wish to use your data partition in both windows or linux except if you are microsoft addicted.

FAT32 + : read/write support on both windows and linux.
FAT32 -  : don't support files larger than 4Gb, don't support unix rights and ownership.

NTFS + : full support under windows.
NTFS  - : Only read support under linux (write support isn't enough reliable), don't support unix rights and ownership.

EXT3 + : reliable, don't need to defrag, full support of unix rights and ownership.
EXT3  - : only read support under windows but many users says here that they never get any problems with the write support but i wouldn't advice a hard use of the ext3 write support under windows

hope you have enough informations to make a choice.

---

### Post by gravediggers on 2006-02-01
[QUOTE=frodon]Really ! : 
 [http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)
 [http://www.fs-driver.org/](http://www.fs-driver.org/)
 [http://digg.com/linux_unix/ext2_3_in..._for_](http://digg.com/linux_unix/ext2_3_in..._for_) windows[/QUOTE]

OK! Perhaps I should have said that ext3 isn't natively supported by XP. You can't expect every person to know about 3rd party enhancements!

[QUOTE=frodon]I advice you to NEVER use NTFS if you wish to use your data partition in both windows or linux except if you are microsoft addicted.[/QUOTE]

Fair enough comment, but XP is more efficient (if you consider XP as efficient at all) under NTFS.

---

### Post by frodon on 2006-02-01
> **gravediggers]OK! Perhaps I should have said that ext3 isn't natively supported by XP. You can't expect every person to know about 3rd party enhancements![/QUOTE]
no problem  said:**
> Fair enough comment, but XP is more efficient (if you consider XP as efficient at all) under NTFS.I agree, that's why i said for data partition because indeed your windows XP partition should be NTFS (no advantages to use FAT32 for your XP partition).

The best solution would be to have full NTFS support under linux and full support of ext3 under windows and i hope it will be the case as soon as possible, but for the moment there's no perfect solution :-?

---

### Post by steve.horsley on 2006-02-01
Under no circumstances should your Ubuntu system root partition be installed on a FAT partition. It just can't hold the necessary file ownership and permissions flags. Use ext3 or ReiserFS. It is also best to keep your /home structure on ext3 or ReiserFS. 

For sharing, I keep a separate fat partition that I mount under /mnt/E, and I symlink it from ~/E for convenience.

---

