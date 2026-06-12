---
title: "Can't resize NTFS XP partition?"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by rmstone1s on 2007-08-05
Ok I searched the forums and found nothing on this one.  I've setup my desktop to dual boot ubuntu and XP and now I want to do the same on my laptop.  When i run the CD (live or alternate) everything goes fine until I go to resize the partition... i select the new partition size (20GB of the total 40GB)... then it says "resizing partition" and the bar is at "0%".... and thats it.... it stops.... never going past 0%.  In the live CD I can cancel the install and start again so its not totally locked up... theres no cancel button in the text version so its frozen and I have to reboot to get out of it.

Any ideas?

---

### Post by wolfen69 on 2007-08-05
try gparted to resize.

---

### Post by annda on 2007-08-05
hmm... defragment the disk under xp maybe?

also, you can try the [gparted live cd]("http://gparted.sourceforge.net/livecd.php") from sourceforge - it's not being developed any more, but it's still very good.

---

### Post by alienexplorers on 2007-08-05
Defragment your XP disk at least twice.  Boot into the live cd and run sudo gparted.  From there you should be able to resize the NTFS partition.

---

### Post by Nike T on 2007-08-05
> **alienexplorers said:**
> Defragment your XP disk at least twice.  Boot into the live cd and run sudo gparted.  From there you should be able to resize the NTFS partition.

I have the same problem as the OP, I followed everything that you told him to do, but it still doesn't work for me, do you know why?

---

