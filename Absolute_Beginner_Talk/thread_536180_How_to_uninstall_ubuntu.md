---
title: "How to uninstall ubuntu ????"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by MEGA. on 2007-08-27
hello guys,

i have two hard disk , i install operating system windows xp sp2 in the first hard , and install ubuntu in the second hard 

but i can't uninstall ubuntu 

need any way to uninstall ubuntu from the second hard

thanks mates:):)

---

### Post by lazyrussian on 2007-08-27
1) Make sure your Ubuntu Hard-drive is mounted/readable (and writable) on your Windows Hard-drive
2) Reinstall The Windows Bootloader using your Windows CD
3) It should automatically boot into your windows hard-drive
4) Format your Ubuntu Hard-drive.

I can't give the detailed steps at the moment, but that's how I'd approach the problem.

---

### Post by peebly on 2007-08-27
> **MEGA. said:**
> hello guys,

i have two hard disk , i install operating system windows xp sp2 in the first hard , and install Ubuntu in the second hard 

but i can't uninstall Ubuntu 

need any way to uninstall Ubuntu from the second hard

thanks mates:):)

Step 1, put your windows xp disk in drive and choose boot from cd rom.

Once the xp disk boots, choose recovery console, select windows drive and type **fixmbr** press enter it will ask you are you sure, **y/n,** when finished type **exit**.

That should remove the grub boot loader.

Step 2, Now boot in to windows xp, and just format the hard disk which had Ubuntu on it.

---

### Post by MEGA. on 2007-08-27
Thanks mates 

i will try this ways 

but the boot file on hard which has ubuntu operating system 

:)

---

### Post by bodhi.zazen on 2007-08-27
Remove Ubuntu (Restore Windows):
	[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

Put the windows boot file as you call it on the MBR (first hard drive, the master HD, the one with windows).

---

### Post by MEGA. on 2007-08-27
> **bodhi.zazen said:**
> Remove Ubuntu (Restore Windows):
	[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

Put the windows boot file as you call it on the MBR (first hard drive, the master HD, the one with windows).


Thanks mate 

this is realy help me 

my regards

---

