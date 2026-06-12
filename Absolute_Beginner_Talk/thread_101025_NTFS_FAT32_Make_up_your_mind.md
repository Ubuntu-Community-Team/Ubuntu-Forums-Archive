---
title: "NTFS? FAT32? Make up your mind"
date: 2005-12-08
forum: Absolute Beginner Talk
---

### Post by adduds on 2005-12-08
Hey all.

Sorry if i'm beating this to death but some people say create as much FAT32 as possible and leave the necessary amount of NTFS for XP. And other people say partition only 2GB of FAT and leave as much NTFS?

What are the differences?

1. Is it true FAT32 can only hold files <= 4GB?

2. Is it true FAT32 corrupts data and is unstable?

3. What do you use?

4. What are you opinions?

---

### Post by kairu0 on 2005-12-08
[QUOTE=adduds]Hey all.

Sorry if i'm beating this to death but some people say create as much FAT32 as possible and leave the necessary amount of NTFS for XP. And other people say partition only 2GB of FAT and leave as much NTFS?
[/QUOTE]

They say that because it allows you space in your FAT32 partition for your data files. Linux can read and write to FAT32 file systems stablely, so this is what I would do (...if I didn't need files > 4GB.)

[QUOTE=adduds]
1. Is it true FAT32 can only hold files <= 4GB?[/QUOTE]

Yes.

[QUOTE=adduds]
2. Is it true FAT32 corrupts data and is unstable?[/QUOTE]

Any file system can corrupt data or unstable. What's more important is the operating system that is using them. Anyway, the fact is that FAT32 uses FAT tables and this compromises their ability to function when they get damaged. (Granted, file systems need some sort of index, but FAT indexes just suck.)

[QUOTE=adduds]
3. What do you use?[/QUOTE]

I only use ReiserFS. If I dual-booted, I would use FAT32 for whatever data files had to be accessible from Windows.

[QUOTE=adduds]
4. What are you opinions?[/QUOTE]

FAT32 isn't incredibly reliable. Linux NTFS support is experimental. Keep a backup of data that has to be on a FAT32 or NTFS partition.

---

