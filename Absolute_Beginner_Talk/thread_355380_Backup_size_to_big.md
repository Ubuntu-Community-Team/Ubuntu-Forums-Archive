---
title: "Backup size to big"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by carverj on 2007-02-07
G'day,
         Am attempting to back up a partition that is 77% full, 9.8G used and 3.6 free!!
Not enough room for tar backup :( 
Is it possible to increase the size of my ext3 partition? 
Is there any other way to back up in this situation?

---

### Post by etank on 2007-02-07
I have used kdar (KDE gui frontend to dar) in the past and it has an option to split the backups to a certain size. I did mine big enough to fit on a CD and then burned the disk and deleted the iso that it created. That way I was able to get the entire backup without running out of space.

As far as resizing a partition look at the [gParted LiveCD]("http://gparted.sourceforge.net/livecd.php") and then also at [resize2fs]("http://www.linuxcommand.org/man_pages/resize2fs8.html").

---

