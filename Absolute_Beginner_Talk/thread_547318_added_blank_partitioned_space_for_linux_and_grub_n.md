---
title: "added blank partitioned space for linux and grub not loading (error)"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by arai on 2007-09-09
as told in [this thread]("http://ubuntuforums.org/showthread.php?t=545879")  i used gparted  to add a  fat32 partition (containing no files) to ubuntu.

what i did was (using gparted)

right clicked the partition and copy and paste to the linux boot drive. this i did in gparted. 

now my system doesn't boot. it says 

[COLOR=Red] grub[/COLOR] loading please wait
error 17

no OS is loading neither windows nor linux. now i am using ubuntu live cd to write this post. please help me.

thanks.

---

### Post by arai on 2007-09-09
is there a way to install grub using the live CD ?

```

sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5227    41985846    7  HPFS/NTFS
/dev/hda2            5228        6628    11253532+   c  W95 FAT32 (LBA)
/dev/hda3            6629        8843    17791987+   f  W95 Ext'd (LBA)
/dev/hda4            8844        9729     7116795    b  W95 FAT32
/dev/hda5            6629        7591     7735266    b  W95 FAT32
/dev/hda6   *        7592        8787     9606838+   b  W95 FAT32
/dev/hda7            8788        8843      449788+  82  Linux swap / Solaris

```

---

### Post by alienexplorers on 2007-09-09
You probably need to reload grub to show its new location.  My directions in my signature line are for loading grub from ext3 partition in Linux.  You may need to change some parts for the FAT32 Partition.  Why in He** did you move it.

---

### Post by arai on 2007-09-10
> You probably need to reload grub to show its new location.

i tried to edit the menu.lst and it is showing a blank file. i think grub is completely gone. now i need to install grub freshly. how to install grub from the start?

---

### Post by arai on 2007-09-10
is it impossible to get back ubuntu and windows xp back as it was there previously ?

---

### Post by Maestro23 on 2007-09-10
> **arai said:**
> i tried to edit the menu.lst and it is showing a blank file. i think grub is completely gone. now i need to install grub freshly. how to install grub from the start?

What is the output from the following command:

> cat /boot/grub/menu.lst (lower case L)

---

### Post by arai on 2007-09-10
can anyone confirm if the my system has linux and windows xp still or they are deleted now ?

using this 

```
sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5227    41985846    7  HPFS/NTFS
/dev/hda2            5228        6628    11253532+   c  W95 FAT32 (LBA)
/dev/hda3            6629        8843    17791987+   f  W95 Ext'd (LBA)
/dev/hda4            8844        9729     7116795    b  W95 FAT32
/dev/hda5            6629        7591     7735266    b  W95 FAT32
/dev/hda6   *        7592        8787     9606838+   b  W95 FAT32
/dev/hda7            8788        8843      449788+  82  Linux swap / Solaris
```

---

### Post by arai on 2007-09-10
Maestro23, here is the output

```
cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory

```also tried this 

```
grub> find /boot/grub/stage1

Error 15: File not found

```

any solutions for me?

---

### Post by arai on 2007-09-10
atleast somebody could tell me** if it is possible or not to get the access to windows and linux**.

so that if it is not possible i could format the entire hard disk and get it work the other way.

this is the big problem with community support. when you are caught up in trouble nobody even bothers to help.

now i am waitinig for somebody to answer this thread.. please note that until then i won't be able to access either win / linux (i am acessing via a live CD). i hope somebody comes forward. please somebody help me to solve this.

---

### Post by vanadium on 2007-09-10
I am afraid that you indeed damaged your system: the Ubuntu installation is gone: you have turned the Ubuntu partition (probably hda6) into a fat partition. You will need to reinstall Ubuntu at this point. The Ubuntu installation will install and configure grub to make Windows available again.

You could just reinstall Ubuntu telling it to use sd6 (this would need to be reformatted to ext3 again!) and the existing swap (hda7). However, since you are at a stage of reinstalling anyway, you could consider simplifying your partition scheme as well before reinstalling Ubuntu. Make sure, before attempting any partitioning, that your have a backup of your user files on a separate drive. As you experienced yourself, the possibility of making an error is never far away while doing fundamental system changes such as partitioning.

---

### Post by arai on 2007-09-10
i am really sad because just a few days back i updated with 180 packages (almost 2 or 3 hours of downloading with a slow connection). 

i will reinstall ubuntu but i don't have the intention to update. let it be the old package till i get the free cd from shipit. 

anyways thanks for your kind reply.

---

