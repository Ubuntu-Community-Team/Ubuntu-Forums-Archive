---
title: "Ubuntu 7.04 does not want to boot after install?"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by tomot on 2007-09-16
I d/led the latest Desktop Edition of Ubuntu yesterday,I then burned the image.
But after the install, when it says to remove the CD, the Ubuntu OS wont boot
from the HD ?

I have a 40 gig Seagate HD dedicated to Ubuntu which I had previously formatted under  XP
using Seagate Diskwizard. (20gig primary, the remainder logical), all formatted fat32
I also gave each partition a volume name  ,Ubuntu c, and Ubuntu d.

When I found that Ubuntu would not boot from the HD I had installed that HD iinto a  secondary position on my computer, I then booted my normal  XP HD   (thank god for removable HD trays)

Running XP I could not see the Ubuntu HD in explorer.  But under Disk Management I found the 
following:

1. the volume names were now missing
2. the primary and logical partitions had been changed by Ubuntu to 35.7gig primary 1.57 gig logical
3. both partitions have no file system showing.

I have done this install twice now, with the same result. 
except the first time I made the entire 40 gig Seagate HD primary.

---

### Post by alienexplorers on 2007-09-16
A ubuntu partition is normally ext2/3.  I am not sure if you can even start ubuntu from a fat32 drive.

---

