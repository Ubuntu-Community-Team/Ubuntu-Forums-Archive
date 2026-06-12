---
title: "Reading files from usb harddisk"
date: 2005-11-28
forum: Absolute Beginner Talk
---

### Post by drgreborn on 2005-11-28
Is it possible to allow winsodws to read a file that is on my portable hdd that was transfered from linux? i.e linux machine -> porta hdd -> windows machine. Thank you very much.

---

### Post by kont.raen on 2005-11-28
[QUOTE=drgreborn]Is it possible to allow winsodws to read a file that is on my portable hdd that was transfered from linux? i.e linux machine -> porta hdd -> windows machine. Thank you very much.[/QUOTE]

Well it depends on the filesystem that you are using on your USB-HDD. Out of the box, windows can only read NTFS and FAT partitions. So if you are using (presumably FAT) one of these, then you just have to plug your disk on while running windows - and that's it.

If your USB-HDD is formatted with ext2/ext3, then you are lucky as there is a driver that you can install to your windows (NT4.0/2000,XP) - allowing you to mount and read an ext2/ext3 filesystem. You can get it here : [http://www.fs-driver.org/]("http://www.fs-driver.org/")

If you are using any other filesystem on your disk (like e.g XFS, JFS etc.) then I am afraid, that you are out of luck.

Hope I could help

---

### Post by drgreborn on 2005-11-28
oops , my apologies. It seems that Kubuntu doesn't write to teh hdd when I do a copy and paste. I have resolved the problems of why I asked this qn. The hdd is on FAT by teh way. Thanks mate.

---

