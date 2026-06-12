---
title: "help!! .. what to do if ext3 partition full (cannot delete trash !!)"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by Average_Joe on 2007-06-25
Hello --

I installed Xubuntu onto a frizzled ancient Win 98 machine to try and help a friend recover files from the FAT32 partition.

The partition I installed Xubuntu onto was the only free unallocated space available to me at the time = 2.7 GB of unallocated space.

So I started moving files from the FAT32 to the ext3 for safe holding.  I didn't notice that when I started to copy files, the ext3 volume had only 530 MB unused space on it.

I filled up my 530 MB space on ext3 pretty quickly, but now I am stuck.  The device (ext3) is full ... I can't move files to it of course but I also can't move files *AWAY* from it.  I can't put stuff in trash, and can't delete from trash.  I can't burn to a CD I guess because of the buffer problem being as there is no room on ext3 partition.

Help??
Is there anything I can do short of re-installing Xubuntu?  (this time after resizing/downsizing the FAT32 partition)

Thanks!!!

P.S.  I tried sudo rm for the file folder but it won't work.  Can I force rm command somehow for a whole file folder?

---

### Post by scxtt on 2007-06-25
you should be able to boot from a live cd, mount the drive w/ the Xubuntu install, and remove files you don't need ...

---

### Post by Rocket2DMn on 2007-06-25
in Nautilus if you hold Shift while clicking Del, it will ask you if you want to permanently delete (forego the trash).
For command line try
```
sudo rm -f filenames
``` to try and force the delete.
Good luck!

---

### Post by Kobalt on 2007-06-25
Maybe you can do a bit of [cleaning]("http://ubuntuforums.org/showthread.php?t=140920") in your packages as well.

---

