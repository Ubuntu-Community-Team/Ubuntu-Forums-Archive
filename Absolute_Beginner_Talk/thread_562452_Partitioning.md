---
title: "Partitioning"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by ozarkman on 2007-09-28
Can anyone point me in the right direction?  I would like to save all my music on a separate portion of my hard drive. I would to be able to reinstall my OS when ever I break it. ( and I break things from time to time.  :) I want to do this without deleting my music every time I reinstall Ubuntu.

I will assume I need to put a fresh install of Ubuntu and at the same time create the space for my .ogg files. Then when the space is created and Ubuntu reinstalled. then rerip my tunes. hopefully for the last time. but I cant seem to figure out how to do this from the Live cd. 

Currently:
                     /dev/sda1 ext3-                     73.10 gig
                     /dev/sda2 extended -             1.41 gig
                     /dev/sda5 swap-                      1.41 gig

---

### Post by Malibu Illusion on 2007-09-28
The answer is to create a separate partition that is mounted at mount point: /home

So, you should have three partitions.

ext3 - mount point: /
ext3 - mount point: /home
swap

The OS is installed on the / partition, while all your settings and files within your /home is located on the other partition.  This way, you can reinstall your OS every day if you want to and even change between distributions and your personal files will remain in tact.

You should reserve maybe 10 GB for the OS partition, ~60GB for the /home partition and the rest in swap.

---

### Post by ozarkman on 2007-09-28
That would work great. But can it be done installing from the Ubuntu live cd?

---

### Post by Malibu Illusion on 2007-09-28
Of course.  You need to select the option to partition your drive manually, then create those three partitions by hand; all possible with the Ubuntu installation disk.  Simply go through the manual partitioning setup and it should be fairly self-explaintory.

---

### Post by ozarkman on 2007-09-28
Thanks I'll give it a try

---

### Post by ozarkman on 2007-09-28
Well my guess is I screwed something up. the system booted and I install gparted to look at the partitions. this is what I have --

dev/sda1 ext3 / - 10.81 gig
/dev/sda2 extended - 63.70 gig
/dev/sda5 ext /home 55.88 gig
/dev/sda6 swap- 7.81 gig

I guess I must be missing some thing.

---

### Post by por100pre1 on 2007-09-28
Please use this command:

```
sudo fdisk -l
```

post the results.

---

### Post by ozarkman on 2007-09-28
> **por100pre1 said:**
> Please use this command:

```
sudo fdisk -l
```

post the results.

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1411    11333826   83  Linux
/dev/sda2            1412        9726    66790237+   5  Extended
/dev/sda5            1412        8706    58597024+  83  Linux
/dev/sda6            8707        9726     8193118+  82  Linux swap / Solaris

---

### Post by por100pre1 on 2007-09-28
> **ozarkman said:**
> Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1411    11333826   83  Linux
/dev/sda2            1412        9726    66790237+   5  Extended
/dev/sda5            1412        8706    58597024+  83  Linux
/dev/sda6            8707        9726     8193118+  82  Linux swap / Solaris

/home and swap are in the extended partition. You could have used a primary partition for /home and the extended partition just for swap.

---

### Post by ozarkman on 2007-09-28
ok I think I might have got it right this time

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1216     9767488+  83  Linux
/dev/sda2            1217        8511    58597087+  83  Linux
/dev/sda3            8512        9726     9759487+  82  Linux swap / Solaris

---

### Post by por100pre1 on 2007-09-29
> **ozarkman said:**
> ok I think I might have got it right this time

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1216     9767488+  83  Linux
/dev/sda2            1217        8511    58597087+  83  Linux
/dev/sda3            8512        9726     9759487+  82  Linux swap / Solaris

Yes, this looks fine. :)

---

