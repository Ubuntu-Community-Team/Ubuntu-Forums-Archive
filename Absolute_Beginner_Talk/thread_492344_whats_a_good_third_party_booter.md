---
title: "whats a good third party booter?"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by rodami on 2007-07-04
Im having trouble booting into vista because my brother deleted the ubuntu partition and nw grub has taken over the disk giving me error 22. Where can I get a good third party booter so I can boot to vista, backup up some files, and reformat the whole thing to avoid this trouble, please help!

---

### Post by ubuntu.daemon on 2007-07-04
grub should still give you the option to boot into vista right??  And howd your bro delete ubuntu  o.O
anyways you should be able to just to another ubuntu install, and write over the old, bc it will show the partitions, vista etc, and will let you create a new grub on the mbr (master boot record), hopefully showing vista, usually would be on the bottom because thats where non-debian file systems get put.

---

### Post by mig5 on 2007-07-04
If you just need to boot vista a few times until you sort the problem out you could make a Windows boot disk on another Windows computer.  Or you could grab the Windows install CD, boot from it, drop into the recovery console and type **FIXMBR**.  Note: if you use that method the only system that will boot is Windows, so if you have any other operating systems be cautious.

---

