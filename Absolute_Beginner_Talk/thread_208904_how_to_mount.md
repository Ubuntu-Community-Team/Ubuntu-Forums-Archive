---
title: "how to mount?"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by penguinKabuki on 2006-07-04
emmm....
i plug in a hdd......type...ext2,i think.coz...the hdd....have fedora 3.
now...i cannot see the partition in ubuntu...
how can i mount it?

---

### Post by TripleE on 2006-07-04
[QUOTE=penguinKabuki]emmm....
i plug in a hdd......type...ext2,i think.coz...the hdd....have fedora 3.
now...i cannot see the partition in ubuntu...
how can i mount it?[/QUOTE]
From the command prompt do "mount /dev/hdd1 /folder/location".  From the gui, System -> Administration -> Disks.

_____________
AMD Athlon64 3000+, 1 GB RAM, Asus A8S-X
BFG Geforce 7300 GS pci-e x16

---

### Post by penguinKabuki on 2006-07-04
now i realize something.....
i cannot open the disk...
i cannot install any software.....but..my access already as the root...hermmm~~

---

### Post by taurus on 2006-07-04
[QUOTE=penguinKabuki]now i realize something.....
i cannot open the disk...
i cannot install any software.....but..my access already as the root...hermmm~~[/QUOTE]
Not sure exactly what you mean you cannot open the disk!  Are you planning to write to it as a regular user?  If yes, then you need to set the right permissions to that new harddrive or only root can write to it.  So, try to use the "sudo" before a command to do that then...

---

