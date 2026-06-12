---
title: "Partitioning question?"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by muted on 2006-05-16
I have ubuntu up and running, but i'd like to try out gentoo.

My HD is 120 gigs, and not anywhere near full. I have currently 3 partitions:
```
#sudo fdisk -l
Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        1824    14651248+  83  Linux
/dev/hdc2            1825       14346   100582965   83  Linux
/dev/hdc3           14347       14593     1984027+  82  Linux swap / Solaris
```

hdc1 (appr 10 gigs) is for /
hdc2 (appr 100 gigs) is for /home
hdc3 (the rest ) is swap


Would it be possible to make a new partition without erasing the data thats already there? Id give gentoo eg 40 gigs taken from my /home partition... is this possible?

Also, could gentoo and ubuntu share the /home partition?

Thankyou!

-Muted

---

### Post by muted on 2006-05-16
Wow, this was meant for the support forum, not the beginners :o 

sorry mods, move?

---

### Post by johnc4510 on 2006-05-16
First back up everything before partitioning anything.
Now, you should be okay resizing your home partition with gparted live cd.
Remember to reduce the size from the end of the partition closest to the swap, or in other words the far right side of the partition. There should be no data there to lose.
Note:Partitioning can result in lost data, be forwarned

---

### Post by muted on 2006-05-16
Cool! Thanks

Now, would i be able to use the same partition (the /home partition) as the home directory for both gentoo and ubuntu?

---

### Post by Jagot on 2006-05-16
[QUOTE=muted]Cool! Thanks

Now, would i be able to use the same partition (the /home partition) as the home directory for both gentoo and ubuntu?[/QUOTE]

It's technically possible but you're likely to run in to some difficulty with configuration files, etc, that are stored in your home directory.

---

### Post by muted on 2006-05-16
[QUOTE=Jagot]It's technically possible but you're likely to run in to some difficulty with configuration files, etc, that are stored in your home directory.[/QUOTE]Oh but i'd have 2 different users for gentoo and ubuntu, its just so i could you know, access my current files easy and have stuff organized nice?

---

### Post by muted on 2006-05-17
bump?

---

### Post by Jagot on 2006-05-18
Well, someone may be able to offer a better solution, but it might be worth creating a storage partition for use between Gentoo and Ubuntu rather than using the same home directory.

---

