---
title: "reading ext3 drive from windows"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by dhawald3 on 2006-10-27
I have windows xp
how can I read or write to ext3 from it??

Is it safe to write to ext3 from windows??

---

### Post by meng on 2006-10-27
Install FS-Drive.

---

### Post by punx45 on 2006-10-27
[http://ubuntuforums.org/showthread.php?t=281399&highlight=ext3+on+XP](http://ubuntuforums.org/showthread.php?t=281399&highlight=ext3+on+XP)

(result from **search**)

---

### Post by jorn on 2006-10-27
You can install adriver in xp to have read and write access to ext2(3):
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by cendant on 2006-10-27
I used FS-Drive - works like charm

One word of warning, though: if you use a specific locale like cp1251, do not move files to ext3 drive first! Only copy

Since the default locale encoding for Ubuntu is UTF8, file names will become corrupted...

I prefer to copy them from/to Windows XP hard drive in Ubuntu - it helps

---

### Post by Claus7 on 2008-06-11
Hello,

just to add that with external hard drives, I plugged the hdd and then I rerun the program, I gave a random name to the drive, and I was able to see its contents. The file system of the hdd was ext3.

Regards!

---

