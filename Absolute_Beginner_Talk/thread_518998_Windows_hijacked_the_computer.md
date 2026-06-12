---
title: "Windows hijacked the computer"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by madddonkey255 on 2007-08-06
After years of use and abuse my family's home computer(Windows) was getting too slow to really do anything and it was driving me insane.  I installed ubuntu and got access from ubuntu to the windows partition with ntfs3.  Then trying to streamline windows I tried to reinstall it and ran into lots of trouble with that, so much that we still get sent to the setup screen.  

Windows got rid of grub when I reinstalled it and I was prepared for that with the super grub and planned on just using that to fix that problem but now I can't log into ubuntu using the grub disk or reinstall grub at all.  Every time I try to reinstall grub or anything it just sends me back to the windows setup screen.  

My main question of course is how I can get grub back, and if reinstalling ubuntu will fix the problem or make the windows situation worse, it's kind of important to get at the files on the computer because we only backed up the truly essential things, and it's killing me to know that the files are there but I can't get at them.

Thanks,
Nolan

---

### Post by bodhi.zazen on 2007-08-06
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Unless you overwrote Ubuntu that should work ...

---

### Post by asmoore82 on 2007-08-06
is the windows disc still in the CD drive?

---

### Post by madddonkey255 on 2007-08-06
No the cd isn't in, ha.  I also tried those instructions for restoring grub with a livecd and it still would go into the windows setup instead of grub.  It seems to me that the windows setup has somehow taken control before grub starts, because there's a white loading line type thing that hasn't shown up before we tried the reinstall.
Thanks,
Nolan

---

### Post by hessiess on 2007-08-06
backup everything and wipe the disk, then start from scratch, unless you want to potentioly resertch for howers/days. there is an ext3 driver for windows to recover data from the ext3 partition

---

### Post by rillip on 2007-08-06
Are you sure you have it set to boot from CD before HDD?

---

