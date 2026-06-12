---
title: "Story so far, might help others?"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by Gris on 2006-07-18
Hi Everyone

I really had quite a learning to get things partially setup on my PC!

I originally had 2 hard drives in my PC, hd0 on IDE and hd1 on a RAID controller. These both had Windows XP on them. The crucial thing I missed was that hd0 was the only one with the Windows boot files (boot.ini, ntldr, ntdetect.com), and hd0 was the one I slected for Ubuntu. There was nothing I needed to keep on hd0 so I happily said go ahead and use the whole drive for Ubuntu - and thereby destroyed the Windows boot files! This orphaned my hd1 drive, and the situation was made worse because I did not realise it needed a special driver to be visible to the system!

The cure was simple in the end: re-install Windows on a small partition on hd0, edit boot.ini on that copy of Windows to include my real Windows system on hd1 and then install Ubuntu on the remaining (majority) free space on hd0. Phew!

I now can boot into Ubuntu on hd0 and Windows on hd1 from Grub easily. Yay!

The only downside is that I have no networking on Ubuntu - only works on Windows. I have a USB D-Link DWL-120d and somehow need to install a driver for this. Off to sleep now, but maybe someone will have a suggestion for me when I awake :)

Cheers

David

---

### Post by Sonic Alpha on 2006-07-18
> **Gris said:**
> The only downside is that I have no networking on Ubuntu - only works on Windows.

Maybe [NdisWrapper]("http://ndiswrapper.sourceforge.net/") can help.

---

