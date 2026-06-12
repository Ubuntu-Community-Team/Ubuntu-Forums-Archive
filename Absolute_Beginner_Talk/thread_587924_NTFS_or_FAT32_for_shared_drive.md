---
title: "NTFS or FAT32 for shared drive?"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by yabune on 2007-10-23
I have a dual boot XP/Ubuntu and I would like to know what's your opinion for the best file system for the shared drive between both OS? Should it be NTFS or FAT32?

The new Ubuntu I know it lets read and write NTFS, but on the other hand FAT32 is supported natively by both OS. What can gives me a better performance? The 4GB limitation of the FAT32 is not a problem for me.

Any tips?

---

### Post by realvz on 2007-10-23
Ntfs

---

### Post by Jorn.jambers on 2007-10-23
In my humble opinion you better use fat32 because its much easier to write to from both OS's
You have indeed the 4GB limitation, but for the rest i dont see much problems. I use also a fat32 partition on my laptop.

Kind regards

---

### Post by mivo on 2007-10-23
7.10 supports NTFS out of the box, so if you use Gutsy, intend to stick with it and don't plan to play with other distros who may lack that support (though getting the extra package is probably always simple), I think NTFS is the more modern approach.

---

### Post by realvz on 2007-10-23
both are inferior...

but at least NTFS is better than FAT32....and writing NTFS files using other distros is not hard at all...
i see no reason why you should use inferior technology when a new one is available

---

### Post by anaconda on 2007-10-23
If you use ubuntu more than XP then I would suggest ext3, and installing the driver for it in XP.

Othervice ntfs is propably better than the annoying fat32..

---

### Post by dptxp on 2007-10-23
If you install ext3 driver in Windows, it will read/write the Linux / partition too.
I do not like Windows accessing Linux.

---

### Post by realvz on 2007-10-23
IMHO...its better to have linux read windows partition than windows accessing Linux things

---

### Post by AliL on 2007-10-23
@ realvz   -   Actually when you install the driver you can choose what partitions the driver can access and you can set it up so it ignores the / partition and only access the shared partition.

@ yabune   -   As I dont think you've yet been told, the driver is called ext2fs and you get it from [here]("http://www.fs-driver.org/").

Hope this helps,
AliL

---

### Post by Sef on 2007-10-23
you can access either [ext2 or ext3]("http://www.google.co.kr/search?q=ext3+for+windows&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a").

---

### Post by mivo on 2007-10-23
Only problem I see with ext2/3 drivers for Windows is that there are apparently none for Vista currently. The OP mentioned he uses XP, so this may not be a relevant consideration, but if he plans on upgrading to Vista in the future, I think NTFS may be the better choice, since Linux won't just stop offering support or drivers. The same may not be true in the reverse direction.

---

### Post by Sef on 2007-10-23
> Only problem I see with ext2/3 drivers for Windows is that there are apparently none for Vista currently. 

If you click on my link in post #10, there is link for Vista being able to read ext2/3.

---

