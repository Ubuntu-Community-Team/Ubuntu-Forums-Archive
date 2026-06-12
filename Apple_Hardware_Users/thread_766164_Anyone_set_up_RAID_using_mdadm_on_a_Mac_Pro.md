---
title: "Anyone set up RAID using mdadm on a Mac Pro?"
date: 2008-04-25
forum: Apple Hardware Users
---

### Post by Pausanias on 2008-04-25
I'm considering buying a Mac Pro to run Ubuntu. The idea is to get three extra 1 Tb hard drives and set the three up as a RAID 5 array. I know you can install Ubuntu on a Mac Pro; however, I haven't read about anyone (successfully or unsuccessfully) setting up RAID using mdadm on a Mac Pro.
This would be a fairly simple setup---RAID 5 on 3 non-boot drives; the boot drive remains non-RAID.

Everything I've read so far *suggests* you should be able to do it. I'm just nervous about plopping down $4K and then finding out that some EFI/BIOS/MBR/whatever weirdness prevents it from happening. So, any of you folks out there currently running mdadm on your Mac Pro?

---

### Post by cyberdork33 on 2008-04-25
> **Pausanias said:**
> I'm considering buying a Mac Pro to run Ubuntu. The idea is to get three extra 1 Tb hard drives and set the three up as a RAID 5 array. I know you can install Ubuntu on a Mac Pro; however, I haven't read about anyone (successfully or unsuccessfully) setting up RAID using mdadm on a Mac Pro.
This would be a fairly simple setup---RAID 5 on 3 non-boot drives; the boot drive remains non-RAID.

Everything I've read so far *suggests* you should be able to do it. I'm just nervous about plopping down $4K and then finding out that some EFI/BIOS/MBR/whatever weirdness prevents it from happening. So, any of you folks out there currently running mdadm on your Mac Pro?

I can't say for sure that it won't work, but I am inclined to say it is very possible that it won't because of the EFI/MBR weirdness... The controller Apple uses is odd and seems counter-intuitive to how things work in other machines... (basically, the partition that you boot from is always promoted to the primary disk no matter the physical attachment, and I would think that would cause havoc for the RAID array). I would definitely get some assurance that it is possible before shelling out the bills for it. Maybe you can borrow some drives from someone and do a test?

---

### Post by Pausanias on 2008-04-25
Yes, I know about the switcheroo with the boot partition. That's why I was planning to have the primary boot drive be a non-RAID drive. So Ubuntu would boot in a standard way.

The idea is after booting Ubuntu off the main drive, it would then mount the three other drives as a RAID-5 array. So, the main quesiton I have is whether there is weirdness about reshuffling of partitions on drives other than the primary boot drive. My gut is that there should not be, but I was hoping for someone with Ubuntu running on multiple internal drives to chime in with their experience.

---

### Post by cyberdork33 on 2008-04-25
> **Pausanias said:**
> Yes, I know about the switcheroo with the boot partition. That's why I was planning to have the primary boot drive be a non-RAID drive. So Ubuntu would boot in a standard way.

The idea is after booting Ubuntu off the main drive, it would then mount the three other drives as a RAID-5 array. So, the main quesiton I have is whether there is weirdness about reshuffling of partitions on drives other than the primary boot drive. My gut is that there should not be, but I was hoping for someone with Ubuntu running on multiple internal drives to chime in with their experience.Sorry for disturbing then. That sounds more feasible to me though. If you boot to the primary drive first, the other drives should default to their "real" placement.

---

