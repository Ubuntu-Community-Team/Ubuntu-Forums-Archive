---
title: "Moving the boot-sector to another disk"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by kraz on 2007-04-25
My HD setup looks as this:

```


Disk /dev/sda: 251.0 Gb, 251000193024 byte
255 hoveder, 63 sektorer/spor, 30515 cylindre, i alt 490234752 sektorer
Enheder = sektorer af 1 * 512 = 512 byte

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sda1       409593240   484359749    37383255   83  Linux
/dev/sda2       484359750   490223474     2931862+  82  Linux swap / Solaris
/dev/sda3              63   409593239   204796588+  83  Linux

Partitionstabellens indgange er ikke i disk-rækkefølge

Disk /dev/hdb: 200.0 Gb, 200049647616 byte
255 hoveder, 63 sektorer/spor, 24321 cylindre, i alt 390721968 sektorer
Enheder = sektorer af 1 * 512 = 512 byte

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/hdb1            2048    51197951    25597952    7  HPFS/NTFS
/dev/hdb2   *    51199155   390732929   169766887+   7  HPFS/NTFS


```

As you can see I /dev/hdb1 and /dev/hdb2 are my old windows system. 
Its time to finally remove it and make this PC a full Linux box with no compromises.

But as it looks to me /dev/hdb has a * meaning it has a boot-flag. How do I move that flag to another disk making Linux boot successfully boot without having to reinstall everything?

---

### Post by kraz on 2007-04-25
Forgot to say that the data on /dev/hdb1 /hdb2 isnt ment to survive anything. They just need to be formatted into EXT3 and mountable

---

