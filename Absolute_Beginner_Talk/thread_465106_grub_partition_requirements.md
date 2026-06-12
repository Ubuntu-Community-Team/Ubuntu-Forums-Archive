---
title: "grub partition requirements?"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by dhawald3 on 2007-06-05
I have just bought Acer 5583 notebook powered by intel core 2 duo T5500.

I plan to dual boot win xp and 2K with Ubuntu 7.04 64bit.

first I will be installing Xp in C: (NTFS) then next partition for 2K.
Ubuntu after that.

I want to know for installing Grub boot loader do u require fat partition??

Or will it install it in C: (NTFS) in which Xp is installed.

please help.

---

### Post by southernman on 2007-06-05
Grub will be installed in the MBR of your hdd. At the end of installation, you'll be told that Ubuntu has found another operating system and asked if you want to install grub in the MBR. That's what you should let it do.

[edited]I think it will show you both xp and 2k [/edited]

---

### Post by dhawald3 on 2007-06-05
> **southernman said:**
> Grub will be installed in the MBR of your hdd. At the end of installation, you'll be told that Ubuntu has found another operating system and asked if you want to install grub in the MBR. That's what you should let it do.

[edited]I think it will show you both xp and 2k [/edited]


what if I have the first partition c: as fat 32 ( without any os in it)

where will the boot loader get installed??

---

### Post by Gina on 2007-06-05
In the first sector of the first physical HD.  The MBR is separate from any filesystem and has a format all it's own.

I've found Ubuntu will find all OSs present including Windows and other versions/copies of Ubuntu and provide multi-boot for all.

---

### Post by southernman on 2007-06-05
The MBR isn't a part of any partition you setup. Can't really explain it, just know that it's in the first few chunks of the hard drive.  Google "mbr" for a plethora of info on what it is and what it does.

As for partitioning anyything fat (16 or 32), I'd steer clear of it. It's horrible and unreliable. Linux now supports not only reading, but writing to ntfs with the use of ntfsg-3. It's an addon package but works well.

---

