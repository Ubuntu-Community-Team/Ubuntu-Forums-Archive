---
title: "Xp/Ubuntu dual boot- XP locking up, Ubuntu OK, but..."
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by joshjani on 2008-02-05
I have successfully installed Ubuntu in a dual boot situation with XP on a cobbled-together half-homebuilt Compaq Pentium III 1.2GHz/512MB RAM machine. Nothing special hardware wise, and Ubuntu seems to run just fine. I'm happy with that part.

Aware that this is an Ubuntu forum, I need help from any dual-boot experts with a Windows problem. Xp seems to lock up after a while in use, while Ubuntu runs stable as can be. I suspected a heat issue at first, as it seems to take a while to hang in XP, but it will invariably do so during a long virus scan, for instance, and many times just will not respond once I've been away from the PC for a while. But if it were a heat issue, wouldn't Ubuntu behave the same way?

It could be that some sort of malware is affecting my XP side, so I wonder- are there any virus/malware scan tools available to run in Ubuntu that can ID Windows problems and deal with them? I cannot mount the XP partition (its NTFS), but I'm hoping there's a tool that can scan for problems regardless.

If not that, can I do a repair install of XP without messing up the partitions and setup I have curently? I figure I can use a "stinger" cd to boot and do a smaller virus scan, then a repair install, but I am hesitant to do anything drastic until I am advised by some of you! 

Thanks-
JC

---

### Post by monkey56657 on 2008-02-05
If you go ahead and reinstall XP then you simply have to reinstall GRUB once its done.

---

### Post by hyper_ch on 2008-02-05
actually you can mount ntfs partitions. Read-only is fairly easy... read-write a tiny bit more complicated.

Regarding AV programs: Most AV scanners on linux do scan for windows viruses.. that's their sole purpose :)

---

