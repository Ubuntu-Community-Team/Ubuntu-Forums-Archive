---
title: "Can't find Vista"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by Crsh on 2007-12-14
I recently installed Ubuntu on my Vista laptop. I intended to dual-boot my computer, instead of switching completely to Vista. However, when I set up grub, I still could not access Vista.

What i want to know is this: If I wiped out the original OS in the Ubuntu install, how can I make sure? (If so, I'll just reinstall Vista).

---

### Post by cotcot on 2007-12-14
See if you find your vista partition back. Look with nautilus in the media folder for you vista or look with ```
sudo gparted
``` if the vista partition is there and how used space is on it.

---

### Post by Sef on 2007-12-14
```
sudo fdisk -l
```

That shows what partitions you have.  If you have Vista there will be an NTFS partition.  It should be on the first partition.  

1) Did you Vista's partitioner to shrink the partition?

2) Did you defrag Vista before installing Ubuntu?

---

### Post by Crsh on 2007-12-14
I tried the code in the terminal, but I received a *'command not found'* error. Also, I've only been using Ubuntu for a few days, and I'm not familiar with nautilus. Any further help would be appreciated.

---

### Post by -grubby on 2007-12-14
you can install gparted by:
```
sudo apt-get install gparted
```

also, you start gparted by :
```
gksudo gparted
```

---

### Post by Crsh on 2007-12-14
> **Sef said:**
> ```
sudo fdisk -l
```

That shows what partitions you have.  If you have Vista there will be an NTFS partition.  It should be on the first partition.  

1) Did you Vista's partitioner to shrink the partition?

2) Did you defrag Vista before installing Ubuntu?

The first partition is Linux. There is nothing that says NTFS or even FAT32. I guess I'll reload Windows and see how that goes. I also didn't defrag or mess with the partitions.

You have just made my day. Buy yourself a cup of Ubuntu on me.

---

### Post by Crsh on 2007-12-14
I've partitioned the disk to allow for the Vista install. When I went to install Vista, though, it said that there wasn't an appropriate partition to install to.

---

### Post by Dark_Stang on 2007-12-14
Vista is going to be a pain to reinstall. I think it wants 40 gigs minimum. It's probably going to trash grub on install as well. You're better off wiping everying, installing vista, partitioning appropriately then installing Ubuntu again.

---

### Post by Crsh on 2007-12-14
> **Dark_Stang said:**
> Vista is going to be a pain to reinstall. I think it wants 40 gigs minimum.

That's strange because my computer shipped with Vista on a 30 GB partition. Still, that sounds right.

---

### Post by Crsh on 2007-12-15
I've increased the partition size to 58 Gigs with Gparted (through the LiveCD), but I still get a message that there isn't an appropriate partition for Vista to install to.

---

### Post by rkd on 2007-12-16
It might help us figure out what Vista doesn't like if you were to do the command

```
sudo fdisk -l
```

again and post the results here.  Remember the parameter to fdisk is a lower case L, not the number 1.  You should be able to copy the output from the terminal window and paste it into the post here.  If you don't want to post from the LiveCD session, you could save the output text to a file on a USB flash drive from the LiveCD session and retrieve it from there when you are ready to post it here.

---

