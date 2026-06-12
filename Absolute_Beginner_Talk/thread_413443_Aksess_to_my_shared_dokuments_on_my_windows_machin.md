---
title: "Aksess to my shared dokuments on my windows machine"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by joramdam on 2007-04-19
When i share a folder on my windows machine, i can't get aksess to them. Ithink it most be someting with read write protection, but not on the windows machine. When i right click on the machine in the workgroup, i get the info that the folder/mashine in the workgroup is write protected ? Can anyone help me with this ?

---

### Post by MrCheese on 2007-04-19
Is this a network share or simply another hdd/partition in your pc? If the latter you can't write to an NTFS partition at all. If FAT you will need to set write permissions for the mounted partition.

If this is a network share make sure the folder is not shared read-only if you actually need write access.

check out this article......

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by joramdam on 2007-04-19
> **MrCheese said:**
> Is this a network share or simply another hdd/partition in your pc? If the latter you can't write to an NTFS partition at all. If FAT you will need to set write permissions for the mounted partition.

If this is a network share make sure the folder is not shared read-only if you actually need write access.

check out this article......

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

It is a network share, and on the windowsmashine it is set to write and read ?

---

### Post by joramdam on 2007-04-19
And if it helps, i can aksess my linux shares.

---

