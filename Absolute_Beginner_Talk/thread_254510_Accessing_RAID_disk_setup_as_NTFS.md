---
title: "Accessing RAID disk setup as NTFS"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by DOD1951 on 2006-09-10
Am running ubuntu 6.06 on desktop with 1 hard disk dedicated to Windows XP and 1 hard disk dedicated to ubunti 6.06. There is also a RAID setup which is configured for use by Windows XP as NTFS. Can I access this RAID via ubuntu and if so how can I do this please?

---

### Post by kidders on 2006-09-12
I may be wrong (ie ignorant, hehe!), but I don't see any reason to expect that a proprietary Microsoft RAID scheme would be accessible using any other operating system :-(

The only way to achieve this level of cross-platform compatibility with RAID is to use a hardware RAID controller ... or perhaps your BIOS has software RAID support (many do, these days). In either case, both Linux and Windows should see your RAID device.

---

### Post by perimere on 2006-09-13
DOD1951,

Presuming the RAID disk isn't a software RAID created in XP.

As described here, for example:
[http://www.techimo.com/articles/index.pl?photo=149](http://www.techimo.com/articles/index.pl?photo=149)

Then you will probably need to get the Linux drivers to be able to use it. Find the brand and model of the RAID controller (it shouldn't matter if it's on the motherboard or a seperate card) and hit the vendors website to see what Linux offerings they have.

The vendor drivers for mine had decent instructions on how to get them working under Linux.

HTH

perimere

---

### Post by DOD1951 on 2006-09-13
Thanks for reply. I managed to get around it for now by ignoring it. Decided I may as well go whole hog and dump Windows XP and let Ubuntu manage the whole setup. What annoys me most is why I didn't discover Ubuntu before now. It's a piece of cake; load it and everything is there. Only had 1 small issue with volume on sound card and that was easy fixed.

---

