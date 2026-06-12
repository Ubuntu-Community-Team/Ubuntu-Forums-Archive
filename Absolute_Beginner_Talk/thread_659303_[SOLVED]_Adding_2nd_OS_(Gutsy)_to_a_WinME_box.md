---
title: "[SOLVED] Adding 2nd OS (Gutsy) to a WinME box"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2008-01-05
I have a dell 4100 box with the primary-master as a 40 gig Windows Millenium OS. I want to add a 2nd hard drive as pri=slave. It has Gutsy installed on it. It was working perfectly as an OS when I removed it from another computer. 

How do I make this work?

How do I prevent M$ from damaging the 2nd hard drive once it is on the cable?

---

### Post by p_quarles on 2008-01-05
> **Mark_in_Hollywood said:**
> I have a dell 4100 box with the primary-master as a 40 gig Windows Millenium OS. I want to add a 2nd hard drive as pri=slave. It has Gutsy installed on it. It was working perfectly as an OS when I removed it from another computer. 

How do I make this work?

How do I prevent M$ from damaging the 2nd hard drive once it is on the cable?
Unless the Ubuntu installation on the drive was working with near-identical hardware (esp. CPU, video, sound), the old installation isn't going to get you very far. Also, without installing GRUB on the primary drive, you're only going to be able to boot Ubuntu via the BIOS (if it supports that at all). You're going to be better off reinstalling. 

Anyway, Windows can't read ext3 partitions without help, and won't do anything to the drive.

---

