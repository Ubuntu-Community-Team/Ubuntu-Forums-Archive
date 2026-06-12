---
title: "Boot loader need help"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Cardmaster91 on 2007-02-11
I've already posted this before, but I can't find the thread, so i need to know again. How do you get the os selections to show up when you start the computer. I just installed windows, and now it always starts in windows.

---

### Post by nickoli_02 on 2007-02-11
You need to reinstall grub, in windows XP. Search the forums, there's a howto somewhere.

---

### Post by meng on 2007-02-11
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Cardmaster91 on 2007-02-11
ok meng, i followed that link. I got to the grub part, but when i put in "find /boot/grub/stage1" it says

Error 15: File not found

---

### Post by meng on 2007-02-11
Have you got more than one hard drive? You better explain the partition setup.

---

### Post by Cardmaster91 on 2007-02-11
ive got one 60.0GB hard drive. (this is not a new drive). I put this ubuntu disk in, and deleted everything on the HD through their partitioner. The very first partition was ubuntu ~30gb, then the ubuntu swap~512mb. then a fat32~5gb (this one is for transferring files to windows). After that I installed it. Then i put in my windows cd and put windows on the rest of the free space. I set windows up, drivers and all. turned off computer, but there was no os selection menu.

---

### Post by meng on 2007-02-11
From the Live CD, show the output of:
sudo fdisk -l

---

### Post by Cardmaster91 on 2007-02-11
```
Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3882    31182133+  83  Linux
/dev/hda2            3883        3943      489982+  82  Linux swap / Solaris
/dev/hda3   *        3944        4554     4907857+   7  HPFS/NTFS
/dev/hda4            4555        7293    22001017+   f  W95 Ext'd (LBA)
/dev/hda5            4555        7293    22000986    7  HPFS/NTFS

```

---

### Post by meng on 2007-02-11
Do you want to overwrite the Windows bootloader? (I would) In that case, don't worry about the "find" command, just proceed straight to:

sudo -i
mkdir /mnt/root
mount -t ext3 /dev/hda1 /mnt/root
grub-install --root-directory=/mnt/root /dev/hda

---

### Post by Cardmaster91 on 2007-02-11
sweet thx, now how to i add windows to the boot menu?

---

### Post by meng on 2007-02-11
Excellent!
edit your menu.lst

sudo nano -B /boot/grub/menu.lst

Add this to the end:
```
title           Microsoft Windows XP Home Edition
root            (hd0,2)
savedefault
makeactive
chainloader     +1

```

---

### Post by Cardmaster91 on 2007-02-11
ok, now how do i save it ur whatever

---

### Post by meng on 2007-02-11
Yes you save it.

---

### Post by Cardmaster91 on 2007-02-11
i know i need to save it, that was not the question. the question was how do i save it? But i resolved it, i just used gksudo gedit /...  and that worked. i din't understand how to use it through the terminal

---

### Post by meng on 2007-02-11
ctrl-x to save. There's a menu of shortcuts at the bottom of screen.
Sorry, misread. But you already solved it anyway.

---

### Post by Cardmaster91 on 2007-02-14
i believe i mentioned something about a blank fat partition i created. I remember having this problem before, but iv'e forgoten how to fix it. The blank fat partition show up in windows (under c:/), but it does not show up in nautilus in ubuntu. How do i add it to the "places" menu? And then how do i create a shortcut that open to the empty partition's folder on my desktop.

O, one more question... well it's sort of windows related. But my main windows drive is I:/. It is not C:/ because i created the empty fat32 before i partitioned windows. My problem is after i installed the drivers (took several hours), i found that a few of the folders were located in C:/ and i failed to find an identical file path in windows I:/. Is it safe do delete the folders in C:/ w/o screwing up my drivers?

---

