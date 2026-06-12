---
title: "HDD Problem after Upgrade"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by sum1cross on 2007-02-17
Recently I updated from Ubuntu 6.06 to 6.10 from a live CD.  Before doing this I archived and backed up my files to my secondary HDD.  Since the upgrade, I haven't been able to successfully use the secondary HDD, and certainly haven't been able to see my archived/backed up data.

I've created a mount point (/media/linuxarchive) and given myself ownership of the folder.  Only folder I see inside the mount point is "lost+found", and when I researched how to view contents of this folder it came back empty.  I can't create folders or write to the secondary either.

fdisk shows:
   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9729    78148161   83  Linux

e2fsck returns (along with other information) 2 directories (which matches what I had on the drive).

Gparted shows 1.3Gb used (2%) of the drive.

Of course, I let Edgy automatically format & partition my (at least I thought) primary drive without checking the table - has it also wiped the secondary?

Any help/advice appreciated.

Thanks

---

### Post by solar george on 2007-02-17
> **sum1cross said:**
> 
Of course, I let Edgy automatically format & partition my (at least I thought) primary drive without checking the table - has it also wiped the secondary?

Sounds like it.

---

