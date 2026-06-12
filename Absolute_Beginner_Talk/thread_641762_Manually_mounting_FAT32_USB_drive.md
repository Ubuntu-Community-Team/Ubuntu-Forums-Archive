---
title: "Manually mounting FAT32 USB drive"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by Wake Rider on 2007-12-15
Normally my fat32 USB flash drive would mount, but I have my 300GB USB NTFS hard drive plugged in and am downloading to it so I can't remove it. For some reason when the Hard drive is plugged in, the USB flashdrive won't mount automatically. How do I mount the flash drive manually without disturbing the 300GB hard drive?? (which is working fine)

---

### Post by rbc on 2007-12-15
First, in terminal, type:
sudo fdisk-l
to see how Ubuntu recognizes the flash drive

---

