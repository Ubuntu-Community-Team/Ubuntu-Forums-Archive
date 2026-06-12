---
title: "Problems with Intel Fake/SoftRAID"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by cprcrack on 2007-10-27
Hello, this is my first post here. I am Spanish so please speak in simple English with me.

I am enjoying Gutsy Gibbon but I had a lot of problems with my RAID0 Volume. Finally, I decided to install Ubuntu in a non-raid disk, and it works fine. The RAID0 volume only contains Windows Vista and installed programs, so I want those two partitions not to appear in my Ubuntu. During the installation of Ubuntu, in "mount point" I write anything (blank) in those two partitions but the first of them (called "Windows Vista") is detected. How can I hide it?

What is strange and worse, is that when I turn off the computer via Ubuntu there is no problem but when rebooting via Ubuntu, GRUB gives me an Error 21. I think the reason is just that Ubuntu unmounts my RAID0 volume!, as I can see in the RAID-BIOS log during the boot of the computer. The problem is solved just turning off the computer, the next time I turn on the computer the RAID0 volume is remounted magically. 

How can I solve this? I have tried with dmraid but unsuccessfully. It could be a bug of GRUB, because I have read something about not supporting "real" RAID... Any ideas?

Thanks.

---

