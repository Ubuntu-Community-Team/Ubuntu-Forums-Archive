---
title: "How does GRUB work if I wipe out Ubuntu on primary hard drive?"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by New-In-Ohio on 2007-08-20
I need some help understanding how GRUB will continue to work if I wipe out Ubuntu.  I'm adding a second hard drive on an already existing dual boot machine (Linux, Windows Xp).  I would like to put all linux distros on the second hard drive and re-partition my current hard drive back to all Windows Xp (I have Norton partion magic).  I'm concerned that the file "menu.lst" is located in /boot/grub which will technically be wiped out once I re-partition.  Will GRUB still continue to work?  Am I about to do something that will make my machine un-bootable from GRUB?  Any help is appreciated.

---

### Post by Diabolis on 2007-08-20
If you have ubuntu on partition A and then you install again ubuntu on partition B, then grub will be always loaded from partition B.

If you install ubuntu on partition A and B, and then uninstall grub from both, you won't be able to boot. But then of you install ubuntu on partition C, grub will be installed and it will recognize partitions A and B. So you actually can mess around with grub if you have enough partitions. You can always fix it.

If you are using an external hard drive, this might be of help.
```
sudo grub
find /boot/grub/stage1
root (hdx,x)
setup (hdx)
quit
```
that will do the right configuration in your latest grub installation. Of course you change the x with the right numbers of your partitions.

---

### Post by louieb on 2007-08-20
You wipe out Ubuntu and you wipe out grub. Unless done right you will not be able to boot.  any questions? [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/") has a very good section on how to uninstall Linux and still be able to boot.

---

### Post by MQMike on 2007-08-20
I do that sort of stuff all the time.  Just think it through on paper and be prepared.  Download Super Grub Disk in case you need it.

Be familiar with the stuff in these 2 references, mainly how to re-install GRUB and how to edit menu.lst.
It’s all very easy to do, trust me.  At any time you wish, you may re-install GRUB to the MBR of the first HD (the Windows drive, called (hd0)) using any of your K/Ubuntu OSs on your second HD (hd1).

It's real nice and easy if both your HDs are IDE or if both are SATA.

Bigpond, GRUB:   [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

Super Grub Disk, new site:  [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)
Super Grub Download List:   [http://forjamari.linex.org/frs/?group_id=61](http://forjamari.linex.org/frs/?group_id=61)

---

### Post by MQMike on 2007-08-20
BTW, the bigpond reference (Herman) discusses Super Grub Disk, too.

---

### Post by New-In-Ohio on 2007-08-20
Thanks for the help. :)

---

### Post by MQMike on 2007-08-20
Yes.

And good luck.  If you run into a problem you need help with, please come back to this same thread so we know what's going on with whom etc.

I would print (hard copy on paper) those two guides out, or at least the best/relevant sections of them, unless you have a second PC.  The SGD Live CD can rescue you from just about anything in this sort of simple setup (2 HDs with XP + Linux).  I just did something very similar.  On the first SATA HD I had XP.  On the second SATA HD I had a bunch of Linux OSs (and GRUB installed to the XP MBR from one of the Linux OSs).  I wiped out the entire 2nd HD (using GParted Live CD partition editor -- free download).  Then installed a new Linux Kubuntu 7.04 to the 2nd HD.  I installed/re-installed the GRUB bootloader to the 1st HD MBR to control the boot menu and the booting of all HDs.  I did make one mistake, but SGD Live CD got me out of it with ease.


fyi:
GParted:   [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
GParted how-to:   [http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

