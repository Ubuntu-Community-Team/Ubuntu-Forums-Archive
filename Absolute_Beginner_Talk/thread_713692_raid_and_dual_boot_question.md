---
title: "raid and dual boot question"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by Repus on 2008-03-03
I’m trying to switch to Linux for day-to-day but have 2 questions

I have a brand new system with nothing installed. I have 2 500g sata drives that I want to install linux on in a raid 1 config. I also have a 120g ide drive I want to put vista on then dual boot.

Raid question:
Ive read several dozen pages about raid but they are either clearly not what im looking for or seem overly complicated. If someone could explain to me, or point me in the direction of a how-to so I can install Ubuntu on the two sata drives in a raid1 setup I would appreciate it. My mobo doesn’t support raid natively but does support AHCI.

Dual boot question:
I would also appreciate advice on how to do this as well. Nearly everything I’ve read seems to assume a single hdd or vista being the primary OS.

Thanks

---

### Post by dstew on 2008-03-03
I have heard that the Alternate Install CD can install Ubuntu to a RAID, but I don't have any hands-on experience with that. If you can get Ubuntu onto your RAID, you should be able to set up a dual boot with Vista on the unRAIDed ide drive. Just install Vista to it, then reconfigure the Ubuntu boot loader to boot Vista. One caution: Vista might try to install itself into one of your RAID disks.

---

