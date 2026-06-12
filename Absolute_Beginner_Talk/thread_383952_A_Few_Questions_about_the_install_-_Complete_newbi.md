---
title: "A Few Questions about the install - Complete newbie. :/"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Vacharin on 2007-03-13
hi i want to dual boot xp and dapper on my machine. i have 2 hard drives. the first one is partitioned in half (xp one one half and hopefully dapper on the other half.) and the other hard drive is ntfs from my old xp computer. i want to use this second hard drive for both OS's 

I get confused when when dapper askes to mount hard drives. i understand to put "/' for the dapper install but what do i put for the xp partition and the second hard drive? to have that second hard drive for both do i put /share for it?

im a little confused please help!

---

### Post by mozkaynak on 2007-03-13
NTFS is not really a good friend of ubuntu.
I dont think you can read/write ntfs with dappler easily.
there are some tricks but I dont know much about them. you can search in the forum by using ntfs keyword.

---

### Post by lamalex on 2007-03-13
dapper will be /(root), xp will be whatever you want, by default /media/hda1 and the share can also be whatever you want, /share works, or /media/hda2, hell name it /giraffe if you want. the name is irrelevant. i would say make it fat32 type.

---

### Post by Vacharin on 2007-03-13
thanks guys. i really appreciate it. oh i forgot to say that there are files on the second hard drive. when i name it /share will i lose files?

---

