---
title: "Uninstalling Ubuntu"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by JollyRoger on 2005-11-14
I want to uninstall ubuntu, and I was just wondering how to do it.  I dual-booted my computer with Windows XP and Ubuntu 5.10.  Do I just format the partitions with Ubuntu on it?  What do I do about the whole grub thing?  Will it just automatically go to windows or do I have to change somthing?

thanks :D

---

### Post by zerhacke on 2005-11-14
If you want to go back to straight windows, this question would be better asked on a Windows forum.

Good luck.  You'll be messing with the rescue command set off the bootable install CD.  I hope you still have your disk.

---

### Post by Kyral on 2005-11-14
1) Sorry to see you go, what was wrong

2) Fastest way to completely NUKE it is to drop in the XP CD, go to recovery mode, and use fixmbr to take out GRUB. Then just format the partitions with your favoritie proprietary tool

---

### Post by JollyRoger on 2005-11-14
How do I use fixmbr to take out grub? is it pretty easy?  Will I still have my info on my windows partition?

The reason I'm switching is because I was having trouble trying to connect to the internet and a few other things.  I think I might just try Linux some other time when maybe my hardware is supported a little bit better (My laptops pretty new), other than that I liked Ubuntu.

---

### Post by Kyral on 2005-11-14
FixMBR will replace GRUB with XP's bootloader

---

