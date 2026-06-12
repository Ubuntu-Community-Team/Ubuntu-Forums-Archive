---
title: "Will expanding its partition make Win7 flip out?"
date: 2012-10-16
forum: Any Other OS
---

### Post by LiamOS on 2012-10-16
I have Windows 7 on my machine which I use for very little, so I gave it 20GB. As it turns out, Windows absolutely eats diskspace, so I need to give it more. If I use gparted to expand its partition, will Windows flip out and refuse to boot?

Thanks,
Liam.

---

### Post by oldfred on 2012-10-16
Possibly.

Better to use Windows to expand it own partition and reboot immediately so it can run chkdsk and update its size. It has its size in the NTFS partition boot sector and that has to match the partition table. Some have reported it working with gparted, but still better to use Windows own MMC.

Use gparted for all LInux partitions and do not use Windows for any thing other than changing the size of its own partition.

---

