---
title: "Uninstalling Ubuntu on a Dual boot, Partitioned Drive"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by mlwillard on 2007-06-10
Hello all, Thanks for your help in advance,

I have installed Ubuntu onto my laptop by using partition magic to create partitions, and I used grub rather than partition magic's 'boot magic' to enable a dual boot. I am running out of space on my disk, and have not been able to enable some hardware on my ubuntu installation. I want to uninstall ubuntu and reclaim the space on the partition. (I'll try ubuntu out on another system later) I've looked at some posts and just want to put together my plan to do so.

I have my install disc, as well as an external floppy drive, but I believe my bios will boot from CD so I want to know if this plan should work:

1. boot from the installation CD, 
2. enter the recovery console (press R when it asks you whether you want to install windows) 
3. at the console, type: fixmbr (which will remove GRUB)

After this does it seem fair to assume I will be able to boot into my installation of windows xp pro, run partition magic, delete my linux partitions, and reclaim my hard disk space?

Thanks in advance,

Michael

---

### Post by ugm6hr on 2007-06-10
> **mlwillard said:**
> 
1. boot from the installation CD, 
2. enter the recovery console (press R when it asks you whether you want to install windows) 
3. at the console, type: fixmbr (which will remove GRUB)

After this does it seem fair to assume I will be able to boot into my installation of windows xp pro, run partition magic, delete my linux partitions, and reclaim my hard disk space?


Assuming you mean the Windows installation CD - then that should work fine.

---

