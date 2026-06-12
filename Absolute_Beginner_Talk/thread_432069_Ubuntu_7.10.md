---
title: "Ubuntu 7.10"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by hectorolivera on 2007-05-03
I made a very bad error. When I upgraded to Ubunto 7.10, I did not migrate the Windows XP info and now I can not boot up into Windows, which I use only for a few features. I have the CD and Access code but don't know how to reinstall it. Can anyone help.

Secondly, I installed Ubuntu, Kubuntu and Edubunto but on my las version, I could change the program to which I wanted to login, on this new version I'm lost.

Also, the printer is not recopgnized and don't know how to go about it.

Please answer my plea for help to:

Hector Olivera at:

[EDIT]Removed e-mail[/EDIT]

---

### Post by galvatron1983 on 2007-05-03
Dont you mean ubuntu 7.04?

I take it your PCs HD has been partitioned? If so you might have done something to the GRUB bootloader....

---

### Post by phr0ze on 2007-05-03
Did you upgrade the proper way? Because when I upgraded I was not asked to migrate my windows settings. This only happened for a new install.

---

### Post by sailor2001 on 2007-05-03
grub is not configured for you...... if you have a live MEPIS disk, or a super grub disk, you can repair grub.......there are other ways also that someone will lead you into

---

### Post by galvatron1983 on 2007-05-03
If your Windows XP is more important to you as it has all of your important docs on it you should use your WinXP installation CD to repair PCs Master Boot Record, which is what GRUB modifies to allow you to dual boot. 

Just boot from the WinXP installation cd, and when you get the installation choices screen choose to enter the recovery console (I think you press R), when you are there type FIXMBR, and itll repair your MBR allowing to boot back into windows.

---

### Post by orb9220 on 2007-05-03
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

---

