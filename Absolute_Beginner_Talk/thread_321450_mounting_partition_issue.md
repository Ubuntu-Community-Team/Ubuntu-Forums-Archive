---
title: "mounting partition issue"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by nibi on 2006-12-18
When i installed kubuntu on my pc i had two hdd with two partitions each (one hdd for windows and one for kubuntu). After installing kubuntu i could access both partitions on the windows hdd as they were listed in storage media as sda1 and sda2.
I just recently repartitioned and formatted the windows' hdd and reinstalled windows. Now there's only one partition but kubuntu still lists sda1 and sda2 in media and neither of them open anything. How do i fix this so i can access windows hdd in kubuntu again?

---

### Post by bodhi.zazen on 2006-12-19
> **nibi said:**
> When i installed kubuntu on my pc i had two hdd with two partitions each (one hdd for windows and one for kubuntu). After installing kubuntu i could access both partitions on the windows hdd as they were listed in storage media as sda1 and sda2.
I just recently repartitioned and formatted the windows' hdd and reinstalled windows. Now there's only one partition but kubuntu still lists sda1 and sda2 in media and neither of them open anything. How do i fix this so i can access windows hdd in kubuntu again?

All we need to do is edit /etc/fstab

To list your partitions:```
sudo fsdiak -l
```

Then to clean up if you will:```
sudo rm -r /media/sda1
sudo rm -r /media/sda2
sudo mkdir /media/windows
```

Then in fstab we will list:> dev/sdxy /media/windows auto user,auto 0 0

Your new windows partition is likely /dev/sda1.

I need to know the file system you used for windows (FAT vs. NTFS) and if you munt ntfs ro or rw. If rw, do you use ntfs-3g ?

---

### Post by nibi on 2006-12-19
I didn't know i could write to ntfs as well. Is ntfs-3g stable, like does it work well or is it really experimental?
and Yes, i use NTFS for windows not FAT (who'd wanna use a non-journaling file system these days? :D )

---

### Post by bodhi.zazen on 2006-12-19
> **nibi said:**
> I didn't know i could write to ntfs as well. Is ntfs-3g stable, like does it work well or is it really experimental?
and Yes, i use NTFS for windows not FAT (who'd wanna use a non-journaling file system these days? :D )

ntfs-3g is reasonably stable, but there are (rare) problems, if you consider wiping windows a problem that is :mrgreen:

At any rate, here is a link to ntfs-3g: [http://doc.gwos.org/index.php/NTFS-3g](http://doc.gwos.org/index.php/NTFS-3g)

---

