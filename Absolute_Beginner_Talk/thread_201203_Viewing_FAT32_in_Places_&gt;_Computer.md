---
title: "Viewing FAT32 in Places &gt; Computer"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by shepherdnick on 2006-06-21
I've got a shared FAT32 partition on my hard drive because that's what people tell me is best to share files between two operating systems, and this was working fine until my shared partition "osshare" disappeared from Places > Computer.  I have no idea why this has happened because it still mounts the partition to /osshare, but I would like to be able to see this as a separate drive in Places > Computer.  Can anyone shed any light onto why this might be happening?

Cheers, Shepherdnick

---

### Post by nanotube on 2006-06-21
if you mount it under /media, then it should show up. (as in, /media/osshare).

---

### Post by aysiu on 2006-06-21
Just go to /osshare in Nautilus (the graphical file browser) and bookmark it. Then it'll show up in Places.

---

### Post by shepherdnick on 2006-06-22
Hmm, yeah that's an easier way to get to /osshare, but before it was like as if it was a separate hard drive... is there a way to get it to act like that?

---

### Post by nanotube on 2006-06-22
[QUOTE=shepherdnick]Hmm, yeah that's an easier way to get to /osshare, but before it was like as if it was a separate hard drive... is there a way to get it to act like that?[/QUOTE]
mounting it under /media should do the trick.

---

### Post by tobeon on 2006-06-28
[QUOTE=nanotube]mounting it under /media should do the trick.[/QUOTE]

How would you go about doing that? (I am having the exact same problem)

---

### Post by Buffalo Soldier on 2006-06-28
[QUOTE=tobeon]How would you go about doing that? (I am having the exact same problem)[/QUOTE]
There are two guides available:[list=1]
[*] [https://help.ubuntu.com/ubuntu/desktopguide/C/partitions-booting.html](https://help.ubuntu.com/ubuntu/desktopguide/C/partitions-booting.html)
[*] [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[/list]

---

