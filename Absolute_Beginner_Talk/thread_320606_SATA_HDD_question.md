---
title: "SATA HDD question"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by kimro on 2006-12-17
Hi all, 

I'm currently running a 40gb IDE as my primary and want to get rid of 40gb, get 2x 80gb SATA and setup:
- 1x 80gb SATA as my primary running Edgy 
- 1x 80gb SATA as my secondary running XP 

I believe in Windows, I have to use the driver floppy before XP can recognize the disk.
Do I need to do the same for Edgy? or is there a native support?

Thank you!

---

### Post by jimrz on 2006-12-17
> **kimro said:**
> Hi all, 

I'm currently running a 40gb IDE as my primary and want to get rid of 40gb, get 2x 80gb SATA and setup:
- 1x 80gb SATA as my primary running Edgy 
- 1x 80gb SATA as my secondary running XP 

I believe in Windows, I have to use the driver floppy before XP can recognize the disk.
Do I need to do the same for Edgy? or is there a native support?

Thank you!

Edgy has no problem with SATA2. Have it installed on this machine along with xp on the other drive and the only issue I had was with the OEM set and the BIOS not playing well with Grub, had to jump through some hoops to get that resolved. Do some research on your specific hardware and BIOS version and you should then know where you stand.

---

### Post by steve.horsley on 2006-12-17
SATA should be no problem, but avoid having both SATA and IDE drives because GRUB and the linux based instsller don't agree on the drive numbers, causing GRUB to look in the wrong place and fail to boot.

---

### Post by Bachstelze on 2006-12-17
Also, I'd recomment installing both OSes on the same drive instead of each on one drive and setup the second for data storage.

---

