---
title: "FAT32 and utf8"
date: 2005-08-14
forum: Absolute Beginner Talk
---

### Post by gord on 2005-08-14
hi;

following the unoffical ubuntu starters guide iv mounted both my fat32 partitions (on diffirent drives you see) as utf8. this works fine for opperations where i am in charge, as i know that the file system is only half case sensitive but for a few of my applications its causing major headaches, espcially applications like azureus in which it seems impossible to download anything at all to the utf8 partitions.

are there any other recomended charsets that will work fine for FAT32 partitions and will my data be corrupted if i change? im english do i don't really need the added capabilitys of utf8.

thankys :)

---

### Post by manicka on 2005-08-14
I use an fstab entry like this and don't have many problems

/dev/hda6       /mnt/win_d    vfat    rw,users,gid=users,umask=000, 0 0

---

### Post by TristanMike on 2005-08-14
[QUOTE=gord]this works fine for opperations where i am in charge, as i know that the file system is only half case sensitive but for a few of my applications its causing major headaches, espcially applications like azureus in which it seems impossible to download anything at all to the utf8 partitions.[/QUOTE]I've experenced the same problem, wanting Azureus to save the torrents to the FAT32 partition but not being able to while being able to read/write to it anyway. Anybody who could shed some light on this would have my thanx as well.

---

