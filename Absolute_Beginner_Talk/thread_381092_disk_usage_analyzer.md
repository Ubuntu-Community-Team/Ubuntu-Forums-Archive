---
title: "disk usage analyzer"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by mgvbstar on 2007-03-10
Hi.  I am using edgy.  I'm a little confused about the information that the Disk Usage Analyzer tool  displays.  In my screenshot, it says that only 5.6 GB have been allocated to /.  My entire filesystem is contained in / so my disk usage should be only 5.6GB.  Then at the top, why does it say that I am using 12.9 GB?  This has puzzled me for a while and I can't seem to find an answer anywhere.  Any help is appreciated, thanks!

---

### Post by aidanr on 2007-03-10
have you any other mounted partitions? it will report those aswell

---

### Post by Kateikyoushi on 2007-03-10
That's your total filesystem usage, means other partitions included.

---

### Post by mgvbstar on 2007-03-10
I do have 2 partitions mounted on /media but I changed the preferences so that those drives would not be scanned (it shows /media to have size only 64KB).  Also, I have ~20GB on the other partitions so it doesn't seem like they are being included.

---

### Post by Kateikyoushi on 2007-03-10
That's what i found interesting in your screenshot, for me it shows the media directorys content as well.
What is the filesystem on those other partitions are those mounted ?

---

### Post by mgvbstar on 2007-03-10
i have a fat32 partition of size 37GB and an ntfs one of size 25GB.  They are mounted, but within the program, under Edit>Preferences I unchecked these two partitions so they would not be scanned.

I guess I should also note that I came across another program called filelight to display disk usage and it gives me the same information.  I don't understand why it's telling me that ~13GB are being used if only 5.6 have been allocated to / ?

---

### Post by Kateikyoushi on 2007-03-10
Please post the output of these.

```
df
fdisk -l
```

---

### Post by mgvbstar on 2007-03-10
df
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             20644348  13522316   6073456  70% /
varrun                 1037260        84   1037176   1% /var/run
varlock                1037260         0   1037260   0% /var/lock
procbususb               10240       128     10112   2% /proc/bus/usb
udev                     10240       128     10112   2% /dev
devshm                 1037260        32   1037228   1% /dev/shm
lrm                    1037260     17580   1019680   2% /lib/modules/2.6.17-10-generic/volatile
/dev/sda5             26218048    165668  26052380   1% /media/ntfs
/dev/sda6             39596896  21107648  18489248  54% /media/fat32
```

fdisk -l


```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3264    26218048+   7  HPFS/NTFS
/dev/sda3            3265        5875    20972857+  83  Linux
/dev/sda4            5876       14593    70027335    5  Extended
/dev/sda5            6398        9661    26218048+   7  HPFS/NTFS
/dev/sda6            9662       14593    39616258+   b  W95 FAT32
/dev/sda7            5876        6397     4192902   82  Linux swap / Solaris

Partition table entries are not in disk order
```

---

### Post by Kateikyoushi on 2007-03-10
> /dev/sda3             20644348  13522316   6073456  70% /

Seems the analyzer is right, your / is 20GB.

---

### Post by mgvbstar on 2007-03-10
right, i know / is 20GB.  My problem was that in the analyzer screenshot, at the top it says that 12.9 GB are being used but in the tree it says that / is using 5.6GB, so where is the remaining 7.3GB?

---

### Post by aidanr on 2007-03-10
yeah, i think we were reading it wrong, it's 5.6 used on / not 5.6 allocated, i can see how that would be confusing with the 100% next to it

---

### Post by mgvbstar on 2007-03-10
thanks for all the help of everyone who has posted here and sorry to keep bothering you with this question, but I still haven't figured it out.

if it means that / is using 5.6GB and of this 5.6GB /usr is using 5GB, /var is using 274MB, etc., then I've got the same question of why at the top it says that 12.9GB is being used. / contains everything so the disk usage at the top should be 5.6

the other way i see to read the display is that / uses 5.6, /usr uses 5, etc. but this doesn't make sense because /usr is in / so the size next to / should include the sizes of all the folders it contains.

if someone could explain explain exactly what the sizes and percentages listed mean, that might clear it up

---

### Post by mgvbstar on 2007-03-11
Solved!!

The problem was that I had ~7GB in /root/.Trash and since I ran the Disk Usage Analyzer from my regular account, this folder was not being accounted for in the tree structure.

---

