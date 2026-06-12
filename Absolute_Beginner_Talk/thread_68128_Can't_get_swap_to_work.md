---
title: "Can't get swap to work"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by nebula on 2005-09-22
Hello,
I've been trying to get my swap partition to work for quite some time now.
I need it because I am running kubuntu with 370mb of memory (512 but 125 taken of for video) and  have only 32 MB left. I presume this is normal (I think it's a lot though?)
I'll just paste my free -m to give some info
```

             total       used       free     shared    buffers     cached
Mem:        386132     370336      15796          0      15240     210312
Low:        386132     370336      15796
High:            0          0          0
-/+ buffers/cache:     144784     241348
Swap:            0          0          0

```
As you can see there is no swap installed to the system at all. However I think I do have it installed to my disk, because my fdisk -l output sees some
```

255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2000    16064968+   7  HPFS/NTFS
/dev/hda2            2001        4802    22507065   83  Linux
/dev/hda3            4803        4864      498015    f  W95 Ext'd (LBA)
/dev/hda5            4803        4864      497983+  82  Linux swap / Solaris

```
Only thing I dont understand is the W95 extended shizzle in there?
At boot time I don't zee anything about my swap at all, though it is in my fstab
```

nebula@lion-0:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/hda5       none            swap    sw              0       0

```
But when I try to use swapon it says
```

nebula@lion-0:~$ sudo swapon -a
swapon: /dev/hda5: Invalid argument

```
Am I completly lost or IS /dev/hda5 my swap partition.

Thanks in advance, Nebula

---

### Post by heimo on 2005-09-22
Yes, hda5 seems like your swap partition. And yes, you should have one, but no, you don't seem to be running out of memory (lots of your memory is used for disk buffering).

I'd try to initialize swap partition:
 ```
sudo swapoff /dev/hda5 (just in case)
sudo mkswap /dev/hda5
sudo swapon /dev/hda5

```

---

### Post by nebula on 2005-09-22
[QUOTE=heimo]Yes, hda5 seems like your swap partition. And yes, you should have one, but no, you don't seem to be running out of memory (lots of your memory is used for disk buffering).

I'd try to initialize swap partition:
 ```
sudo swapoff /dev/hda5 (just in case)
sudo mkswap /dev/hda5
sudo swapon /dev/hda5

```[/QUOTE]
 aha so it was make swap I was missing.
```

root@lion-0:/home/nebula# free -m
             total       used       free     shared    buffers     cached
Mem:           377        371          5          0         53        168
-/+ buffers/cache:        149        227
Swap:          486          0        486

```
Thank you very much!

---

### Post by hiperactive on 2005-09-23
Thanks!! I had almost the same problem (installed ubuntu without a swap partition) and it helped me a lot. Finally the swap space is working.

---

