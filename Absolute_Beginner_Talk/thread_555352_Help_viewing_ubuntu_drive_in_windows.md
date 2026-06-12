---
title: "Help viewing ubuntu drive in windows"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by sam510 on 2007-09-20
Well I had to reinstall windows, and I backed up alot of my files my ubuntu desktop. So when I try to get my files from the ubuntu srive I dont see the second ubuntus drive in my computer, Before when I used to duel boot windows xp and vista I was able to go into vistas drive from my computer. It would show XP as C: and vista as D:, How can I retrieve my files??

P.S I also tried going on ubuntu and dragging my files on the windows drive but it said i couldnt modify any files on that drive.

---

### Post by lisati on 2007-09-20
You might find that accessing Windows folders easier with Ubuntu than the other way round. This is because it's easier for Ubuntu to access the NTFS file system used by Windows than for Windows to access the ext2/ext3 file system used by Ubuntu.

One solution might be as follows:
[LIST=1]
[*]Set up a folder on your Windows partition to be used to store files from Ubuntu
[*]Install ntfs-3g on Ubuntu
[*]From Ubuntu, copy files to your Windows folder
[/LIST]

---

### Post by jordanmthomas on 2007-09-20
[http://www.fs-driver.org](http://www.fs-driver.org)

Is this what you're looking for?  This allows you to read (and write to) ext2/3 partitions in Windows, and it's a breeze to install and configure.  You can even assign it a driver letter.

---

### Post by sam510 on 2007-09-20
> **jordanmthomas said:**
> [http://www.fs-driver.org](http://www.fs-driver.org)

Is this what you're looking for?  This allows you to read (and write to) ext2/3 partitions in Windows, and it's a breeze to install and configure.  You can even assign it a driver letter.

Wow thank you very much worked like a breezex2

---

### Post by alienexplorers on 2007-09-20
Use Ext2IFS_1_10b.exe to read and write files from windows to ubuntu.  Use ntfs-3g to read & write files from ubuntu to windows.

---

