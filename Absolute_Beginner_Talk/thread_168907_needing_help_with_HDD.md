---
title: "needing help with HDD"
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by Balle on 2006-05-01
hello, i'm new to these boards and linux.
i have recently partitioned my HDD in three 1. for windows 2. for ubuntu (newest version) 3. for data.

but when i use the Ubuntu OS i can't view the Data partition, what can cause this? 

is it because it is NFTS? if so, what type does it have to be, and can i change that without deleting the intire partition?


thx for your time and replys


Balle

---

### Post by pbaehr on 2006-05-01
NTFS is read only from Ubuntu. So that wouldn't prevent you from seeing it, just from editing it. An easier choice for shared data between a Windows and Linux install is fat32. Unfortunately, you can't change it without losing the information stored on the partition.

When you say that Ubuntu "can't view" the partition, what exactly do you mean? Is it giving you an error saying you don't have permission to view it? Or is it just not available at all?

---

### Post by zerhacke on 2006-05-01
[QUOTE=Balle]hello, i'm new to these boards and linux.
i have recently partitioned my HDD in three 1. for windows 2. for ubuntu (newest version) 3. for data.[/QUOTE]
It's actually probably partitioned in five.

1, windows
2, ext2 for Ubuntu
3, logical partition
4, swap partition inside the logical
5, data

Use ```
fdisk -l
``` in a terminal to find your partition structure.  Then you need to mount the data partition using ```
mount -t ntfs /dev/hda(partitionnumber) /mount/point
```Where (partitionnumber) is the partition number the data partition is and /mount/point is the location you want to mount it to.

---

### Post by Balle on 2006-05-01
yes it is 5 partitions, and i'm almost sure they'r how you said.


where do i write the codes? i cant see a bar anywhere, like with some other linux systems

---

### Post by pbaehr on 2006-05-01
To get to a terminal press ctrl+alt+F1 (F1-F6, really). To get back to the desktop hit ctrl+alt+F7.

---

### Post by steve.horsley on 2006-05-01
[QUOTE=pbaehr]To get to a terminal press ctrl+alt+F1 (F1-F6, really). To get back to the desktop hit ctrl+alt+F7.[/QUOTE]
That works, but when you want to cut and paste between the command line and a browser window, as when posting the results of running a command, it's easier to use a command window in the GUI. It's under **Accessories->Terminal**.

---

### Post by pbaehr on 2006-05-01
Sure, if you want to do it the SENSIBLE way! ;)

---

