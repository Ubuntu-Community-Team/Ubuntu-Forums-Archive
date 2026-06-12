---
title: "Dual Boot Trouble"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by boomba05 on 2006-06-07
I've searched and searched for this, but I can't find a solid answer anywhere, at least that I understand.  I apologize if this is a repeated post.

I currently have WinXP installed on a pair of Raptors in Raid0.  I have two more 40gb IDE drives as secondary drives.

I installed Ubuntu on a partition in the master IDE drive, and everything went smoothly, the computer rebooted, and I awaited the boot menu.

However, the computer booted right into Windows.  I tried numerous different ways to try to get a boot menu to show, but nothing worked.  I've done dual boots before, but never with Raid0 or SATA drives.  Also, at the end of the install process, it told me that it found WinXP and was adding Ubuntu to the MBR.  I used the advanced install CD, not the regular one.

I also tried to just install Ubuntu into the Raided Raptors on a partition, but during the install process, it threatened to erase everything off the drives, so I chickened out.

Any tips on bringing up a boot menu?  I still have Ubuntu installed on the IDE drive, and Partiton Magic sees it there, so I'm a little lost.

Thanks in advance!!


P.S.  It's 64bit, if that changes anything.

---

### Post by r3st on 2006-06-07
go into the BIOS and check the boot order of the drives

---

### Post by uzi09 on 2006-06-07
yeah, try what r3st says and also MS's MBR usually has problems displaying linux stuff. if i were you i'd get grub instead.

just stick the ubuntu install cd in there, go to install (advanced/expert mode) then scroll down to grub and install it from there. it should get it working properly.

let us know how it went

---

