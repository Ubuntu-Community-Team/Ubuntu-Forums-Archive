---
title: "Files copied to FAT32 won't show in XP"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by tuqann on 2006-12-19
Hi,
I'm duel-booting XP and Dapper, sometimes, especially with large quantities of files, if I copy them from an external source (say a CD or an external harddrive, and sometimes from my Home folder) to my FAT32 partition, boot XP and try to access the files, they are not there.

If I created a new folder to place them in, the folder is also missing. The strange thing is my FAT32 root is spammed with fsch00000(numbers).rec files that are actually those I tried to copy.

Any idea why this happens and how to avoide it?

---

### Post by bodhi.zazen on 2006-12-19
> **tuqann said:**
> Hi,
I'm duel-booting XP and Dapper, sometimes, especially with large quantities of files, if I copy them from an external source (say a CD or an external harddrive, and sometimes from my Home folder) to my FAT32 partition, boot XP and try to access the files, they are not there.

If I created a new folder to place them in, the folder is also missing. The strange thing is my FAT32 root is spammed with fsch00000(numbers).rec files that are actually those I tried to copy.

Any idea why this happens and how to avoide it?

only thought I have is that you need to unmount the device from Linux.

I share a usb device with linux/windows and have never had this problem.

Also see this: [http://www.fs-driver.org/](http://www.fs-driver.org/)

This will allow direct access from windows.

WARNING: Scan all downloaded files for viruses before you transfer them from Linux to Windows.

---

