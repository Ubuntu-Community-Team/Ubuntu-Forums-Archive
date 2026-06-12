---
title: "Question about partitioning"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by Mabes on 2006-01-12
Hey all, I have just built a new pc, and since I realized I left my windows disc at school, and because a couple friends of mine keep suggesting it, I'm trying linux for the first time.  So far, it's kinda neat.  But anyways, what I'm wondering, is that I want to have part of my hard drive partitioned to ubuntu, and the rest of it for windows (xp home edition).  The question I have, is should I put windows on first, and then ubuntu, or ubuntu on first, or does it not matter?

Currently I have just ubuntu, but I just went through all the default install options, so it's partition takes all of the hard drive (minus the small logic files part).  I'm guessing I will have to remove this when I put windows on, but is it possible to resize the ubuntu partition?

Thanks ahead of time for any responses!

---

### Post by milstead on 2006-01-12
Both ways are possible. Windows will overwrite the grub boot loader (making ubuntu unbootable) so it is sometimes better to put windows on first and then ubuntu. That said it is possible to restore grub by booting from a linux rescue disk/cd chroot'ing to your existing linux system and reinstalling grub from there.

Some other things to note: Linux can only read from Windows XP NTFS partitions. It can not write to them (there are tools to attempt this, but trust me they suck and you wouldn't want to trust your data to them). Windows XP can use FAT32 paritions which linux can both read from and write to. I have installed Windows XP on NTFS but use a FAT32 partition for all the Documents and Settings folder. This requires an unattended type install of Windows XP since you can not easily move this folder after installation. You could always just keep your My Documents on the FAT32 partition as this is easy to move in Windows XP. Windows XP seems to run happier when it is the only primary partition on the disk. I tend to put the Linux paritions (and the fat32 paritions) in an extended partition or on another disk.

I don't know if you can resize ext3 and other linux paritions. I'd be surprised if you couldn't. Give qtparted a look or use the more scary fdisk command line tool.

To do these things you'll need to do some googling around for some tutorials. I'm afraid I haven't got time to repeat there work here, but if you have any quick questions I'll be happy to answer them next time I come by.

Hope this helps,

Timie Milie

---

### Post by Chris Tucker on 2006-01-12
[QUOTE=milstead]I have installed Windows XP on NTFS but use a FAT32 partition for all the Documents and Settings folder. This requires an unattended type install of Windows XP since you can not easily move this folder after installation.[/QUOTE]

.. its quite easy to move the my docs folder.. right click it on the desktop or start menu -> properties -> move.
i found this quite handy when my sister was living here and using two computers, and wanting her files accessable from both. (this was before i got ubuntu) there are similar easy ways to change the docs and setts folder entirely. but the my docs folder is the main one anyone would want to move and thats easy.

---

