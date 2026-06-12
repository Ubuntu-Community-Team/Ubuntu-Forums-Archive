---
title: "Uninstall Ubuntu??"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by icyblue on 2007-06-21
Hello,

I don't know how to uninstall Ubuntu from my system.. I've a 80GB Hard disk partitioned into 4 drives(20GB each). I've windows xp in one drive(C:\) and have given 10GB to ubuntu in another drive(D:\) with remaining 10GB space is with windows itself and rest two drives are having some other stuff. I want to uninstall Ubuntu completely and give that 10GB space to windows itself. How exactly should  I do that?

Thanks for any assistance!!!

---

### Post by taurus on 2007-06-21
Use GParted LiveCD to delete those Ubuntu partitions.  Then, merge them with your XP.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Zzl1xndd on 2007-06-21
As a side note if you want to leave it as a seperate partition you can do that as well format it into a Windows friendly format, Oh and in either case you may wish to use your Windows CD's repair MBR to remove grub and replace the windows boot loader.

---

### Post by icyblue on 2007-06-21
So, I cant do anythin only with ubuntu cd in hand? To let you know, I don't have my Xp CD now with me...Anything else you can suggest???

---

### Post by Zzl1xndd on 2007-06-21
> **icyblue said:**
> So, I cant do anythin only with ubuntu cd in hand? To let you know, I don't have my Xp CD now with me...Anything else you can suggest???

From my inderstanding it is going to depend where gtub is installed you can use the ubuntu CD to wipe the Partition that Ubuntu is on but if grub is there then you wont be able to boot.

---

