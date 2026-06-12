---
title: "Formatting 2nd Hard drive"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by Autolycus on 2008-04-14
I have Ubuntu installed on one hard drive. I have a second hard drive installed in my computer for use as data storage. How to I format this drive and get it recognized on the desktop.

---

### Post by Trollslayer on 2008-04-14
See [COLOR="Red"]fdisk[/COLOR], this lets you create/edit/delete partitions.

---

### Post by Znort_Ubern00b on 2008-04-14
you need gparted

should be able to get it from synaptic manager.

---

### Post by Het Irv on 2008-04-14
ext3 is the filesystem that Ubuntu uses, you can format it using gParted.
I know that it on the Live CD, but I cannot remember if it is installed by default.
```
sudo gparted
```
and if that fails
```
sudo apt-get install gparted
```
then retry step 1.

---

### Post by lackofcreativity on 2008-04-14
Do what one of them said, and format it as FAT, FAT32, ext2, or ext3. I've heard that 7.10 can write to NTFS, but since you have no way of defragging it, I advise against it.

---

