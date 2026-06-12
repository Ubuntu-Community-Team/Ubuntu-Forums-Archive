---
title: "Grow my ext3 ubuntu paritian"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by tjb891 on 2006-12-16
I have a 20gb ext3 partition for my main ubuntu partitian. I now have 20GB of unallocated space on the same hard drive. Can anyone tell me how to grow the partition?

---

### Post by Kobalt on 2006-12-16
Hello,
You will not be able to enlarge a partition, I don't think so, and to be honest I wouldn't recommend you to do it. If I were you I'd create a new partition on which I'd store whatever I want... It's safer. You can do this by starting the a LiveCD session, then use Gparted (it's in System > Administration menu) to create your new partition. Make it a FAT32 if you want to share this partition with Windows (if you have a dual boot) or an etx3 if you only use Ubuntu (or Linux in general). 
Then, here is how you can get your partitions avaliable in Ubuntu : 
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s02.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s02.html)

Cheerio !

---

### Post by Bachstelze on 2006-12-16
Partition resizing works very well.

**tjb891**, could you please paste a screenshot from GParted so we can see exactly how your drive is partitioned ?

---

### Post by Kobalt on 2006-12-16
You can actually enlarge partitions ?? I thought that wasn't possible... I still think creating a new partition is a better idea though.

---

### Post by jolene on 2006-12-16
At the same time, do you think I could have similar advice? (ntfs = Windows, ext3 = Ubuntu). I want to give Ubuntu as much space as possible, and make Windows go sit in a corner and think about what it has done.

[ATTACH]21141[/ATTACH]

---

### Post by smoker on 2006-12-16
if the unallocated space is next to your ext3 partition this is as easy as a couple of clicks of the mouse in gparted. if not, it is still very possible, and if you paste a screenshot as Hymnto Life stated, someone will easily guide you through the process.

---

