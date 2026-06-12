---
title: "windows partitions has gone!"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by baytuni on 2006-01-27
Hi
I had two hd's one is SATA other is IDE. SATA is partitioned into 4 parts(6 including swaps) and IDE one is single partition. I had a XP on /dev/hda1 and another on /dev/sda1. Then i decided to use ubuntu and installed it on /dev/sda3 and grub on the IDE drive's boot sector.Two or three days later (i did nothing but updates) both hda1 and sda1 were gone. (Even xp doesn't see them.) But only the partitions which has os's(xps) on them went. The other ntfs partitions which i use for storage have no problem. I want to rescue my partitions they were important for me. How could it happened. Can i rescue them.Thanks for help!

---

### Post by Kapre on 2006-01-27
[QUOTE=baytuni]Hi
I had two hd's one is SATA other is IDE. SATA is partitioned into 4 parts(6 including swaps) and IDE one is single partition. I had a XP on /dev/hda1 and another on /dev/sda1. Then i decided to use ubuntu and installed it on /dev/sda3 and grub on the IDE drive's boot sector.Two or three days later (i did nothing but updates) both hda1 and sda1 were gone. (Even xp doesn't see them.) But only the partitions which has os's(xps) on them went. The other ntfs partitions which i use for storage have no problem. I want to rescue my partitions they were important for me. How could it happened. Can i rescue them.Thanks for help![/QUOTE]

baytuni - get a livecd (Ubuntu or Knoppix) and use pop it in. Check if the hd/partitions are detected. If they are, you can rescue the hd. With regards to why this has happened, I dont have any idea.

K

---

