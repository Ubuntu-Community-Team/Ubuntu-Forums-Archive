---
title: "Install Problem (JMicron???)"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by Agrajag27 on 2008-03-31
Okay, in this thread:

[http://ubuntuforums.org/showthread.php?t=740331]("http://ubuntuforums.org/showthread.php?t=740331")

I mentioned my frustration at installing Ubuntu. I've since spoken with an Ubuntu network admin I trust who went through various approaches and said I have a "JMicron" issue.

This is an Intel BX2 motherboard. That's Intel-branded, not just an Intel-based board. It most likely does have the JMicron controller.

Is anyone familiar with this issue enough to provide a solution?

At this point Ubuntu is sitting on an IDE drive that the BIOS sees as HD0 (It shares space with my F partition that has all my music on it). Windows is on a SATA drive that the BIOS sees as HD1.

I used the Alternate CD to install (LiveCD wouldn't boot) and all seems fine. GRUB, however, never appears so reboots just go back into Windows. We were able to get GRUB to come up with some changes but then we killed NTLDR and lost Windows before repairing it.

It stinks to be this close. The only time I've seen a Linux GUI is when I got GPARTED to boot to do some tweaking.

---

