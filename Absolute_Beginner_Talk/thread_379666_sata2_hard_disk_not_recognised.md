---
title: "sata2 hard disk not recognised"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by arsadogi on 2007-03-08
i checked posted threads about sata rcognition problems and i coudn'nt figure out.If there is somthing i can do to set up my HD manualyi would apreciate that.

MB:asus m2r32-mvp
CPU:amdX2 4200
graphics:asus eax x1600
hard disk:WD 160gb sata 2.0

---

### Post by Bachstelze on 2007-03-08
The problem is not in your HD but in the SATA chipset of your MOBO.  Since it's fairly recent, it might not be supported by Dapper's 2.6.15 or Edgy's 2.6.17 kernels. You might want to try Feisty, which I've heard is very usable now and runs the latest 2.6.20 kernel, which might support your chipset.

---

### Post by arsadogi on 2007-03-10
i'm trying to install Edgy Eft AMD64.During installation there is no HD recognition meanwhile i had successfully installes windows xp.So there is no hardware problem.I tried other distros to but i faced the same problem.During ubuntu installation i noticed that i can provide sata drivers
using a floppy disk.BUT..first i must find the proper drivers for my sata 2.0 controller.where is the drivers OEO??:lolflag:

---

