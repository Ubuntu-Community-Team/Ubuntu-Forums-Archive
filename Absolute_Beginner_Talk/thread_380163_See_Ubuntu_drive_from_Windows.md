---
title: "See Ubuntu drive from Windows"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-03-09
I'm dual-booting XP and Dapper Drake. When I installed Dapper, it very kindly put a shortcut to my Windows partition on the desktop. 

But of course I can't see my Ubuntu partition in Windows. Is this possible? The Windows partition I want to see is FAT32.

---

### Post by benfindlay on 2007-03-09
Right click on My Computer and choose Manage. Then go into Disk Management. There should be a partition in there without a drive letter if it is FAT32. Just give it whatever letter you want!

---

### Post by maxamillion on 2007-03-09
You just need a utility that apparently Microsoft will sell you ..... or you can just run the community supported free alternative found [here]("http://www.digg.com/linux_unix/ext2_3_indexed_file_system_read_write_support_for_windows")

EDIT: I think I read your post wrong, but the link I gave is to be able to see a linux partiton of ext2 or ext3 filesystem from windows.

---

### Post by Kateikyoushi on 2007-03-09
With this driver you can read and write ext partitions from windows. [LINK]("http://www.fs-driver.org/")

---

### Post by benfindlay on 2007-03-09
If its FAT32 like you say, then you won't need any drivers. However, ubuntu makes its partitions ext3 by default, so unless you've changed this then you WILL need external software to get access to it

---

### Post by freesitebuilder on 2007-03-18
Im trying Linux Reader from [http://www.diskinternals.com/linux-reader/product.shtml](http://www.diskinternals.com/linux-reader/product.shtml) which is freeware.

---

