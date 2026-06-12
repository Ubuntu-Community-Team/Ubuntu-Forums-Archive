---
title: "Writing to Linux Box with ext3  file system from Windows XP with NTFS"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by noobie2 on 2006-10-10
Hi 
I installed Dapper Server over the weekend and installed the GUI and WebMin.  I also installed SAMBA. 

I have a general question.  If I want to save a file located on my XP machine to the Linux box, does SAMBA do the file conversion for me?  Or do I need a FAT32 partition on the Linux box that both machine can read and write to?

I want to use the Linux box as a server so i really want to avoid 3rd party software loaded onto the Windows boxes to view and write to Linux.

I have read several SAMBA HOWTO's but they all seem a little confusing :(

thanks for any advice

---

### Post by Kateikyoushi on 2006-10-10
There is no need to convert anything, the machines communicate through samba, I can copy to ubuntu from windows without any extfs driver.

---

