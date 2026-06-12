---
title: "resizing partition"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by TumbiWan on 2006-09-12
I recently installed ubuntu to a partition of a drive shared with windows. I like ubuntu a lot.  So, I made more room for it on the drive, but I cannot resize the partition.  Little help.....?

---

### Post by Obor on 2006-09-12
You cannot repartition mounted drive so the best thing is to use a live cd. you can use the ubuntu live cd or [Gparted Live CD]("http://gparted.sourceforge.net/livecd.php")

Some people prefer other things but GParted is what I used, its simple and works fine (i think its the same one that is used on ubuntu cd)

---

### Post by Timothy Butwinick on 2006-09-12
Indeed it is the same: 
Read this thread [http://ubuntuforums.org/showthread.php?t=255315](http://ubuntuforums.org/showthread.php?t=255315)
Note, however, that you only have to copy the files (as the last three or so messages say) if the free space is **before** your Linux partition and you want to keep the data on it. Otherwise, you can just resize it to fill upp the free space.

---

### Post by erniet on 2006-09-12
You could create a seperate partition again and use that for storage

---

### Post by Timothy Butwinick on 2006-09-12
But then he can only use it for storage, right? All programs are installed in the /bin directory, which is on the system partition, or have got this wrong?

I prefer not having to think about where I put my files.

---

