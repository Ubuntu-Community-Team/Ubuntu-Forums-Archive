---
title: "fs of external hd?"
date: 2008-06-12
forum: Apple Hardware Users
---

### Post by spigolo on 2008-06-12
hi,
i need to buy an external hd, it will be used both under osx and linux. it seems that at the moment the only fs that works read/write for both operating systems is hfs+ not journalled. is there any other hint or advice to know?

thanks.

sp

---

### Post by abhiroopb on 2008-06-12
Fat32 should work, as should ntfs. I honestly suggest ntfs. I have two 320GB hard drives, and I have heard from a lot of different sides that I should have formatted it to ext3. But think about it like this. I have both hd's full of stuff, now if it was formatted to ext3 I could only browse it in linux (you can browse in windows with ext3 drivers, but it isn't an ideal solution). So if you ever fill up your HD and decide to use some other OS (like windows) you may run into problems.

---

### Post by cyberdork33 on 2008-06-12
> **spigolo said:**
> it seems that at the moment the only fs that works read/write for both operating systems is hfs+ not journalled.That is not correct, in fact, I would not recommend using HFS+ because of issues with Linux.

FAT32 is the most compatible, but has a 4GB filesize limitation. NTFS works well with MacFUSE in OS X, and in Ubuntu.

---

### Post by owlgorithm on 2008-06-25
NTFS is not natively supported by Mac, but FAT32 is -- and FAT32 is most likely going to be the default format of the drive. So, don't worry about it, it should just work on both sides.

---

