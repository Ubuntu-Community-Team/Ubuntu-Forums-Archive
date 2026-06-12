---
title: "Windows 8 vs Grub"
date: 2012-10-28
forum: Any Other OS
---

### Post by PaulInBHC on 2012-10-28
I had XP on an IDE drive. Added a SATA drive and installed 12.04. On boot I got the grub menu with 12.04, recovery, memtest, and XP.

I upgraded to W8. Several reboots later all was well except it still listed XP on the grub. I restarted today from W8 and my bios screen says it can't read the SATA drive. I unplugged it and still couldn't boot into W8, I get a grub rescue> prompt.

I ended up inserting the XP disc and fixmbr. Now I am in W8.

Any ideas?

---

### Post by PaulInBHC on 2012-10-28
I think the SATA drive died. I plugged it back in and still cannot be detected by bios.

---

### Post by PaulInBHC on 2012-10-29
I wonder if the EFI in W8 is preventing the SATA with ubuntu from being read?

---

### Post by oldfred on 2012-10-29
UEFI is hardware based. It has replaced BIOS or in most cases UEFI will also allow BIOS boot. You cannot install Widows 8 in UEFI mode on a BIOS/MBR system, it just runs like Windows 7 then in BIOS mode.

If BIOS does not see a drive it is a hard ware issue. Double check connections. Whenever I opened case with the old parallel wide cables I managed to partially disconnect the connection by bumping something. It might look connected but  a good push then did reconnect it. 
Also switch cables with good known working one. Sometimes they fail.

---

### Post by PaulInBHC on 2012-10-29
Thanks for the help. I see EFI files in the boot folder of Windows and was hoping that it was a software problem. I already tried unplugging and plugging. I'll try different cables now.

I ponder sending back a new HDD with my info on it.

---

### Post by TheMTtakeover on 2012-10-29
> **PaulInBHC said:**
> Thanks for the help. I see EFI files in the boot folder of Windows and was hoping that it was a software problem. I already tried unplugging and plugging. I'll try different cables now.

I ponder sending back a new HDD with my info on it.

Who are you sending it back to and how sensitive is the information?

Perhaps try something from here
[http://www.tomshardware.com/forum/255458-32-erase-data-dead-hard-drive](http://www.tomshardware.com/forum/255458-32-erase-data-dead-hard-drive)

---

### Post by PaulInBHC on 2012-10-30
It is a Western Digital. Going back to them. Website states that they wipe the drive as part of their testing procedure.

I tried plugging it in alone without the other drive and different cables.

I'm going to plug it into my other box first to verify that it is dead.

---

