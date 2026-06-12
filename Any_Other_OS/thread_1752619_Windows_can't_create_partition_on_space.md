---
title: "Windows can't create partition on space"
date: 2011-05-08
forum: Any Other OS
---

### Post by Maheriano on 2011-05-08
I just bought a pile of new hardware, put it together, and installed Ubuntu 11.04 all in about 90 minutes. Then I spent 90 minutes trying to get past the first screen on the Windows installer......WTF?

I left a 100 GB space formatted to FAT32 to install Windows 7 on. When I popped in the CD and booted into the Windows installer, it said it can't create a new System partition on the disk, the allocated space was Logical. So I booted back into Ubuntu, changed it to NTFS, tried again, same result. So I booted back into Ubuntu, deleted it so it was completely unpartitioned space, tried again, same result.

So I've got this 100 GB of Logical unpartitioned space on my terabyte drive that I would like to install Windows 7 on but I have no idea how to do it. It wants a System partition.

---

### Post by jocko on 2011-05-08
It's probably a lot easier to install windows first, then Ubuntu.
The windows installer will overwrite the boot loader, preventing ubuntu from booting (but you can fix this afterwards with the help of an Ubuntu live cd).

From the error message you get it seems like your free space is within an extended partition (hence whatever partition you try to make in the free space will be a logical partition, not a primary). Windows needs to be on a primary partition, and that partition may also need to be the first partition of the drive (at least that was true for previous versions of windows).

If you haven't spent too much time configuring Ubuntu, I would suggest you remove all partitions from the drive and start over by installing windows first. Just leave some free unpartitioned space for installing Ubuntu.

---

### Post by yetiman64 on 2011-05-08
> **Maheriano said:**
> I just bought a pile of new hardware, put it together, and installed Ubuntu 11.04 all in about 90 minutes. Then I spent 90 minutes trying to get past the first screen on the Windows installer......WTF?

I left a 100 GB space formatted to FAT32 to install Windows 7 on. When I popped in the CD and booted into the Windows installer, it said it can't create a new System partition on the disk, **the allocated space was Logical**. So I booted back into Ubuntu, changed it to NTFS, tried again, same result. So I booted back into Ubuntu, deleted it so it was completely unpartitioned space, tried again, same result.

So I've got this 100 GB of Logical unpartitioned space on my terabyte drive that I would like to install Windows 7 on but I have no idea how to do it. It wants a System partition.

I'm not totally sure about win7 but previous versions of Windows required a Primary partition only and would not install to a logical partition, I suspect it is still the same though. 

Even changing to NTFS won't help as you are still trying to install on a logical partition.

---

### Post by Elfy on 2011-05-08
moved out of ubuntu support forums

---

