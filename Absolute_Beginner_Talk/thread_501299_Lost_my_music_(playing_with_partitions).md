---
title: "Lost my music?? (playing with partitions)"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by javier.ldb on 2007-07-15
So i think i screw my partition and/or file system (ext3). When i mount it, only shows four non-sized files with wierd  names. I try Testdisk, and after Analyze, i can see the folders and files, then i write, reboot, remount, but nothing happens.

Any ideas? Its my entire music collection there, i'll apretiate ANY help.

---

### Post by whizbaby on 2007-07-15
> **javier.ldb said:**
> So i think i screw my partition and/or file system (ext3).
Could you please precise how exactly you 'screwed' partitions? Which programs/commands did you use to achieve this masterpiece?

---

### Post by Malta paul on 2007-07-15
If you can see your files you haven't zapped them, you just need to assess them.
Can you post the results of  " sudo fdisk -l  "

---

### Post by javier.ldb on 2007-07-15
Hi again. This is my "fdisk -l /dev/hda"
```
Disco /dev/hda: 80.0 GB, 80026361856 bytes
16 cabezas, 63 sectores/pista, 155061 cilindros
Unidades = cilindros de 1008 * 512 = 516096 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hda1   *           1      155056    78148192+  83  Linux
```

The complete description of my problem can be found [COLOR="RoyalBlue"][here]("http://ubuntuforums.org/showthread.php?t=499512")[/COLOR]

Thanks to you guys for the replies!

Javier

---

