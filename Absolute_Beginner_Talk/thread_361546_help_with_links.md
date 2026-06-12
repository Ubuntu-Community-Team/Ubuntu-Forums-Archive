---
title: "help with links"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Cardmaster91 on 2007-02-14
Um... i don't really know how to explain this, but at flixflux.co.uk, there are quicklinks to the torrent files, how do i open these with azureus by default. i know if i saved them i could, but how do i do it with the open option?

and i also need to know how to create links to folders. 

P.S. one last thing i need to know, is how do i make a fat32 partition i have created visible in nautulis?

---

### Post by annda on 2007-02-14
1. save one torrent, open it with azureus as default application and restart. should help.

2. middle-click a folder and drag it to where you want to have the link - when you release the mouse button, choose Link here.

3. [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Cardmaster91 on 2007-02-14
part 1 and 2 worked good. i don't quite understand part 3. my file doesn't really look anything like theres, can u simply tell me what to add to the file?

---

### Post by annda on 2007-02-14
ok, what happens when you type

```
sudo fdisk -l
```

just copy and paste the message. this can help us find the right options for your fstab file.

---

### Post by Cardmaster91 on 2007-02-14
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

