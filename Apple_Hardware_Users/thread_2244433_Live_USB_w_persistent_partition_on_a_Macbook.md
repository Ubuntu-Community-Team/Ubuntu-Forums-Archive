---
title: "Live USB w/ persistent partition on a Macbook"
date: 2014-09-16
forum: Apple Hardware Users
---

### Post by andi6 on 2014-09-16
I think i've tried like 10 different tutorials on how to create a Live-USB-Drive with or without tools like Unetbootin, Mac Linux USB Loader and so on.
Some did work, most didnt. What worked best in terms of hardware compatibility and load time was:

1. Converting the ISO to IMG
2.
```
[FONT=Menlo]sudo dd if=xubuntu-14.04.1-desktop-amd64.img.dmg of=/dev/rdisk1 bs=1m[/FONT]

```

Is there any way to use this version of creation and also create a persistent partition on that usb drive? I tried with partitioning the drive beforehand with one fat32 partition and one ext4 partition (named casper-rw). dd seems to delete this partitions and also makes the USB-Stick unreadable by gparted and diskutility.
Im using a 32GB flash drive, so i want to use a partition instead of a max. 4GB casper file to hold the persistent files.



Thanks and cheers

Andi

---

