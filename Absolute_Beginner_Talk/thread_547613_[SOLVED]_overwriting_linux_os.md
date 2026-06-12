---
title: "[SOLVED] overwriting linux os"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by josiano on 2007-09-10
Hi all!

I am totally new in Linux, I've searched but couldn't find any answer on this forum.

I have a windows/pclinuxos dualboot and I want to overwrite my pclinuxos with Ubuntu.
I also want to keep my windows partitions for a while.

When I am installing Ubuntu, under the partitionning part, I already have my (ext3) "/" and "swap" partitions, but I also have on the same disk several NTFS partitions, and I don't want them to be erased !
So my question is, wich option is best ? :

1- Don't touching anything on these and leave default settings.
2- Setting their mount point to "/windows".
3- Setting them to "don't use".

I first selected "don't use", but at the last part of the installation, I was warned "All the informations on the partitions you erased(?) will be lost."

Thanx for your help.

_j.

---

### Post by AusIV4 on 2007-09-10
As I recall, when you manually partition the device from the installer, it gives you a list of all partitions. This list has check boxes to indicate whether or not the partition should be formatted, and a text box indicating where it should be mounted. So long as you don't check the "format" box, it shouldn't matter whether or not you give them a mount point, your data will be fine.

---

### Post by LaRoza on 2007-09-10
> **josiano said:**
> Hi all!

I am totally new in Linux, I've searched but couldn't find any answer on this forum.

I have a windows/pclinuxos dualboot and I want to overwrite my pclinuxos with Ubuntu.
I also want to keep my windows partitions for a while.

When I am installing Ubuntu, under the partitionning part, I already have my (ext3) "/" and "swap" partitions, but I also have on the same disk several NTFS partitions, and I don't want them to be erased !
So my question is, wich option is best ? :

1- Don't touching anything on these and leave default settings.
2- Setting their mount point to "/windows".
3- Setting them to "don't use".



Assuming you don't want anything on the PCLinuxOS partition, manually set up the partitioner, and select the EXT3 partition (PCLinuxOS) as / and swap as swap. Install.

Ubuntu will add Windows to the boot menu, and PCLinux will be overwritten.

You have to manually select the target partitions, don't use the preset options.

I haven't used the GUI installer for a while, so I don't know exactly what it will look like, but it is easy.

---

### Post by josiano on 2007-09-10
ok, I'm gonna test it right now then.
Thank you ! :)

---

