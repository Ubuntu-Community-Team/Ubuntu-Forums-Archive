---
title: "dual boot problems"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by kolva on 2007-07-08
i just installed ubuntu and am dual booting with ubuntu and winxp and when i start up my computer it goes to the grub dual boot screen and if i select windows it goes to a screen that only says 
Starting Up... 
_      

and stays there forever and never starts windows, is there any way i can get windows to work...i don't have the cd anymore and i have a lot of files on there i need...please help......thnx:confused:

---

### Post by confused57 on 2007-07-08
> **kolva said:**
> i just installed ubuntu and am dual booting with ubuntu and winxp and when i start up my computer it goes to the grub dual boot screen and if i select windows it goes to a screen that only says 
Starting Up... 
_      

and stays there forever and never starts windows, is there any way i can get windows to work...i don't have the cd anymore and i have a lot of files on there i need...please help......thnx:confused:

If you can boot into Ubuntu, I recommend that you burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
SGD may be able to boot Windows or restore Window's IPL to the mbr...

---

### Post by kolva on 2007-07-08
thanks...ill try it

---

### Post by Warren Watts on 2007-07-08
> **confused57 said:**
> If you can boot into Ubuntu, I recommend that you burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
SGD may be able to boot Windows or restore Window's IPL to the mbr...

  I recently installed Edubuntu in a dual boot configuration onto a second hard drive of a computer that had Xubuntu already installed on the primary drive, and the install corrupted GRUB.  I downloaded the floppy based version of the Super Grub Disk and was able to use it to restore GRUB to working order.  

  It appeared to me that SGD was written in spanish and ported to english, which made some of the onscreen prompts a little confusing, but I stumbled through it and managed to fix things without too much trouble, and I'm pretty much a Linux/Ubuntu newbie.

---

### Post by kolva on 2007-07-08
i can't get sgb to boot on startup... idk if im doing it wrong...i am using a flash drive and i have the usb sgb file on it and i set it to be the primary boot device and it still goes to the same screen and winxp wont work......do you know any i can get files from that partition of my hard drive over to my ubuntu partition and then just wipe the windows partition....im not worried about windows xp....im worried about my 40+ gb of music and games...

---

### Post by kolva on 2007-07-08
hey....i think i might have also found another problem.....when i installed ubuntu i told it to partition 55.8 gb of the hard drive apart from the rest and thought that was the partition that it would go on...but i think it went to the larger partition and forced windows to the other one...could that have caused this problem....

---

### Post by kolva on 2007-07-09
actually...could anyone tell me how to get rid of ubuntu and keep the winxp partition intact so i can reinstall ubuntu and not screw up the partitioning this time... if anyone could help that would be great:confused:

---

