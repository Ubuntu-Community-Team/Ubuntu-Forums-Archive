---
title: "harddisk usage"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by pataphysician on 2005-11-14
when i do *fdisk -l* i get the following:

```

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device      Boot     Start      End      Blocks     Id    System
/dev/hda1            5473        7296    14651280    83    Linux
/dev/hda2   *           1        5284    42443698+   83    Linux
/dev/hda3            5285        5472     1510110     5    Extended
/dev/hda5            5285        5472     1510078+   82    Linux swap / Solaris

Partition table entries are not in disk order

```

i'm pretty sure that when i was installing, i told ubuntu to just use the whole disk however it saw fit. i don't *think* i chose to create an ~12gb partition at the end of the drive. i'm not really sure why it's there. i tried to mount it, but was told i need to specify a file system. i don't know how to find that out, so i guessed ext2, 3, and reiserfs, but all of those failed. is it possible to recover that space somehow? preferably, can i tack it on to the end of hda2, to make that partition larger?

also, hda3 and 5 seem to be the same area on the drive. out of curiosity, why is it listed twice?

---

### Post by shof2k on 2005-11-14
/dev/hda5 is used as virtual memory, and so isn't directly accessable to you.  It used if ubuntu runs out of available memory, then data is written from memory to this swap disk. 12GB is very large, usually, 2 to 4 times your RAM amount is enough.

/dev/hda3 is an extended drive....think of it as an envelope holding logical drives inside it.  It is the logical drives that you actually read and write from, hence you have /dev/hda5 inside /dev/hda3.  (As far as I know, IDE type drives have a 4 partition limit and the extended partition is used as a way around it)

You can alter partitions using fdisk or a graphical tool like 'gparted'.  Just remeber to back up your data before hand!.

Hope that helps :)

Again you can use fdisk or gparted

---

