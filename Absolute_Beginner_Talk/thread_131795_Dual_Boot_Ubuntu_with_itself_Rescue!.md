---
title: "Dual Boot Ubuntu with itself? Rescue!"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by darf681 on 2006-02-17
I was wondering if anybody had ever done a dual install / dual boot of Breezy with Breezy.  That way, if you screw up one, you can boot to the other to get online and find out how to fix your primary...

thanks!

:)

---

### Post by mp3guy on 2006-02-17
Its not that hard, just make sure you've got another partition and install away, grub with recognise both OS's

---

### Post by nalmeth on 2006-02-17
I say why use up the space? Just hold onto a liveCD if you need to rescue your system, or make your /home on a seperate partition, and reinstall if needed.

---

### Post by darf681 on 2006-02-17
That's a good idea, I hadn't really thought of that.. and I already have /home on a separate drive altogether.

sweet.

---

### Post by Almighty on 2006-02-17
Wow with having all the trouble with my oringinal Ubuntu partition, just had that idea of using a live disc backup to restore my system. I will try it tonight when I get home.

---

### Post by bonzodog on 2006-02-17
Some of us Dapper testers are dual booting with breezy, that way, when dapper screws up and becomes unbootable for what ever reason, we can boot into breezy and rescue it from there. I'm not, because I am confident of how to rescue the system should anything major fall over (fingers crossed!)

---

### Post by Almighty on 2006-02-17
Well I have tried to create a total system back up using a live CD but it seems as though this computer likes to freeze. I guess its back to the drawing board for me.

---

### Post by aysiu on 2006-02-17
It's a great idea, especially when you're new.

As long as you have two partitions, you can do it quite easily.

Install Ubuntu Breezy on one partition and install Grub to the MBR.

Then, install Breezy on the other partition and install Grub to the MBR (overwriting the first Grub). This new Breezy installation should automatically add the first one to the boot menu.

It's a good idea because you can have one *stable* Breezy that you use on a daily basis. Then you can have another *test* Breezy to install and uninstall software that may break your system--you can play around without ruining the functionality on your other Breezy.

---

### Post by cotcot on 2006-02-17
Just to say I have done the dual breezy on 1 disk (and triple breezy on 2 disks) with the obejective aysiu explains (testing). One of the test was upgrading breezy to dapper, but that was not succesfull (dapper flight3). 
So i installed dapper over it. (see my PC2 in the signature)

---

