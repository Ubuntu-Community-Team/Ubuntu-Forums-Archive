---
title: "how to start windows (grub error 17)"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by TisKicking on 2007-03-11
For a while, I had a dualboot xp-ubuntu on my laptop. But today, I wanted to remove ubuntu, so I deleted the partition on which ubuntu was installed. I could of known that this would happen, but now GRUB doesn't work anymore (error 17). 

How can I start windows xp without the xp cd (i only have recovery disks, but i don't want to lose my data) and without a floppy drive? I've already tried to start to boot with win98 files on a USB stick, but that didn't work either.

what can i do?

---

### Post by RizSilverthorn on 2007-03-11
If you can get hold of a proper install CD for XP, boot off it, but choose to run recovery console (can't remember the exact option, don't have XP disks any more). After logging into the DOS prompt, type > fixmbrthen> fixboot. This will replace the GRUB bootsector with the Windows XP one. When you reboot it should boot into Windows.

---

### Post by Herman on 2007-03-11
I agree with RizSilverthorn, if you can borrow a Windows XP install CD from a friend.

You don't have to use use FIXBOOT though, only FIXMBR.

FIXMBR is for putting the pointer in your MBR to make it point to your Windows partition. The MBR is written to with the stage1 code for Grub.

FIXBOOT is for repairing your Windows boot sector, which isn't touched by Grub at all, you can do that if you want but it won't be useful.

I have computers that only have 'Recovery disks too and I have done it many times from a Windows 98SE boot floppy disk, it does exactly the same job but you use the  fdisk /mbr command instead. That works for XP just as well as '98.

There are lots of other ways to do it, a few more are listed and explained step by step for you on this web page, [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

Regards, Herman  :)

---

### Post by devilzdad on 2007-03-11
Formatting the partition, to FAT32 filesystem, in whch u used to install ubuntu will also solves the problem......

---

