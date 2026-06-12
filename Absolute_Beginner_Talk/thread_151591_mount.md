---
title: "mount??"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by belikralj on 2006-03-28
can you mount from and to any directory or only /dev/ to /media/ or /mnt/??

also when mounting file systems, my floppy doesn't auto mount like the cd-drive but when I mount it manually I have to specify the file system. I can read and coppy from it but can't write so my other Ubuntu (or the one that wrote the data) can read it, what's going on? Can I not specify autodetect for floppy mounting and file system or will I have to be stuck doing it manually every time?

Thanks in advance!

---

### Post by taurus on 2006-03-28
You can mount it anywhere you want.  For instance, you can do something like this if you wish,
```

sudo mount -t vfat /dev/hdb1 /data1

```
If you want to write to it, you need to be root so use "sudo" then!!!

---

### Post by IDipSkoalMint on 2006-03-28
Something I found out last night was in order to have it automatically mount for you, you need to go in and edit the FSTAB file. You can get an idea of what you need to do from page 2 of my thread [here]("http://www.ubuntuforums.org/showthread.php?t=151448&page=2"). You probably just need to modify the instructions to fit your need. Best of luck ;)

---

### Post by infoseeker on 2006-03-28
This site explains it pretty well ---->

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by belikralj on 2006-03-28
Thanx, the links helped a lot! And so did you.

Thanx again

---

