---
title: "[SOLVED] Installing UB7.10 over UB6.06"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by marioub on 2008-02-28
I'm new to ubuntu and I need help. I have windows xp on my machine.
I'm using a dial up modem and loaded Ubuntu 6.06 as a dual boot system.
I purchased Ubuntu 7.10 on a dvd disk and want to load it in place of 6.06.
Is there any way to delete 6.06 so that I may reload 7.10?

I haven't done anything with 6.06 so I don't need to save anything.
I obtained the instructions to clean load for 7.04, but they give options for partioning that I can't perform on 7.10 partitioning software.

Can I just delete the Ubuntu partions in windows xp and then do a clean install of 7.10?
My concern is what happens to the old dual boot (Grub setup) scenario?

---

### Post by A4006 on 2008-02-28
Just boot the 7.10 LiveCD and install 7.10 to the partition that you made for 6.06.  If you want to resize or format the said partition, use gParted (I believe this comes on the 7.10 LiveCD). GRUB will work fine, since when you install 7.10 it updates/reinstalls GRUB and will detect both 7.10 and XP.

---

### Post by Joeb454 on 2008-02-28
I don't think you'll be able to delete the Ubuntu partitions from Windows XP.

Though the Ubuntu 7.10 DVD should be able to boot up as a Live DVD. So you can use Ubuntu without installing it.

You can open the partition editor from System>Administration and erase the Ubuntu Partition from there (it'll be ext2 or ext3 format) and then install Ubuntu 7.10.

GRUB will be done by the 7.10 installer :)

---

### Post by marioub on 2008-02-28
I want to thank both A4006 and Joeb454 for your assistance.
I used Windows XP disk manager to delete the 6.06 partitions and then used the Ubuntu 7.10 installation disk and it came up with a different partitioning scenario and it all worked just fine.

I have a different problem now. The older version used the complete screen real estate but 7.10 uses about 3/4 of it. So I guess I'll investigate to see if a thread has been start (or I'll start one). Thanks again!!

---

