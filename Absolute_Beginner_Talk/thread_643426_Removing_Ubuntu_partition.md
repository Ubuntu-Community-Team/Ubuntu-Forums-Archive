---
title: "Removing Ubuntu partition"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by linkhows on 2007-12-17
I have a 60 gb harddrive with half of the space for Windows XP and the other half for Ubuntu and I need to delete Ubuntu of my PC because it is messing with my dvd burner.  I don't have a Windows XP installation disk and I'm not sure if I need it to fully remove Ubuntu or get back partioned harddrive space. So I guess my question is how do I remove Ubuntu without using a Windows XP install disk?

---

### Post by Landrovan on 2007-12-17
Just use a partition manager like partition magic while running in your windows system

In those software, you can remove and reformat partition

---

### Post by Presto123 on 2007-12-17
I have had too many issues with Partition Magic, you might not, though. 

I have used GParted for this kind of stuff.

Would you rather have someone help you with the DVD burner issues instead? Because someone could probably help with that.

---

### Post by wjp.reg on 2007-12-17
> **linkhows said:**
> I have a 60 gb harddrive with half of the space for Windows XP and the other half for Ubuntu and I need to delete Ubuntu of my PC because it is messing with my dvd burner.  I don't have a Windows XP installation disk and I'm not sure if I need it to fully remove Ubuntu or get back partioned harddrive space. So I guess my question is how do I remove Ubuntu without using a Windows XP install disk?

You will need [Super Grub Disk]("http://supergrub.forjamari.linex.org/") to remove the linux partition and then restore the windows MBR so it will boot after grub has been removed along with the linux partition.

Super Grub Disk is a live CD and works with linux and windows.  Use it AFTER running gparted live to remove linux/resize windows.

good luck.

---

