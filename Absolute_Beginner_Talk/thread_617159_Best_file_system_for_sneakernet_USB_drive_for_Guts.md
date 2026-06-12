---
title: "Best file system for sneakernet USB drive for Gutsy, XP and Leopard"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by badmigraine on 2007-11-19
1. What would be a file system recommendation for the case where an external USB drive is a backup library of, say, 200+GB of .jpegs, and you want to be able to plug it into different machines running Ubuntu, XP and a Mac (Leopard)? The goal is to be able to  import the .jpegs onto each machine, so the users can play with them on each machine's photo file management and editing software. 

Assumptions:
--no network, so no Samba/NAS;
--read/write functionality desired for all machines, but is only absolutely required for the Ubuntu machine.
--speed/features of file system not as important as stable, reliable cross-functionality with Linux, Windows and OSX

Is it just FAT32, and maybe NTFS?


2. Any conventional wisdom on which brands/OEMs of USB external drive like Ubuntu best?

Thanks!

---

### Post by derred on 2007-11-19
NTFS is the way to go IMHO since it does offer some protection in the case of power loss and so on, but I don't know for sure if you can read/write to it from Leopard. On the other hand, if you do choose vFAT be sure you know that it has several limitations such as the 4GO/file limit and the fact that it doesn't support file by file encryption and/or compression.
I also found this tidbit:> ...the guy that developed NTFS-3g (stable ntfs driver for linux with full write support) was hired by Apple. He will obviously be porting it for OS X...
And there is a MacFUSE project, I just don't know how well implemented it is.
Somebody pointed to > [http://idisk.mac.com/shadowofged/Public/Software/NTFS-3g/NTFS-3G%2020070116-r3.dmg](http://idisk.mac.com/shadowofged/Public/Software/NTFS-3g/NTFS-3G%2020070116-r3.dmg)
But I haven't tried it since I don't have a Mac anymore.

To answer the recommendation part of your question:
I have a WD MyBook Premium ES External 320 and It came pre-formated as a single 298GO fat partition with 300mb of Windows and Mac software. Nothing for poor old Linux but since it's now a single ext3 partition we can just call it even.

---

