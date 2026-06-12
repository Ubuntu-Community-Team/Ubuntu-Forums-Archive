---
title: "External hard drive"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by TinWoodsman on 2007-04-15
I bought a external hard drive case, and put a hard drive that I have used before, with ubuntu installed on it. It lets me read the drive content, but will not let me wright to it. It keeps telling me that I do not have permission. I would like to reformat the hard drive and use it to back up my files.

I hope someone out there can help...

Thank you..
TinWoodsman

---

### Post by zekopeko on 2007-04-15
alt+f2 

then type

```
gnome-terminal
```

the in terminal type 

```
fdisk -l
```

and copy & paste the output here. make sure that the drive is connected and powered on

---

### Post by bobplano on 2007-04-15
can you clarify what you want to do? do you want to just wipe the drive and use it for backup purposes? to reformat it the live cd has GParted and you can delete and make new partitons for the drive.

---

### Post by TinWoodsman on 2007-04-15
Disk /dev/sda: 30.7 GB, 30736613376 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3581    28764351   83  Linux
/dev/sda2            3582        3736     1245037+   5  Extended
/dev/sda5            3582        3736     1245006   82  Linux swap / Solaris

---

### Post by TinWoodsman on 2007-04-15
Can I install Gparted, and them reformat?

---

### Post by bobplano on 2007-04-15
Gparted is on the live cd and if you try to use gparted with the hard drive you'll probably run into mounting issues because you are using the partitions

---

