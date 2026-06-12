---
title: "Swap file without Linux"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by JPWheless on 2007-10-18
I'm trying to install 7.04 on a computer with only 256 MB of RAM. All I have is the live Cd, and I would really prefer not to download the alternate install CD, because we have really limited bandwidth.


Is there a way to create a swap file with Gparted, with the Live CD, or with Windows?
BTW, this is a dual-boot system with one hd.

---

### Post by Technoviking on 2007-10-18
The live CD should work fine (maybe a little slow) under 256 MB.

---

### Post by bobplano on 2007-10-18
i don't see much of a problem here. the live cd is supposed to be able to run off like 192mb of ram. and yes, gparted was included with the live cd last time i checked so you can make a swap partition with that

---

### Post by -grubby on 2007-10-18
the live-cd should work fine, albeit slowly with 256 MB or RAM. I'm pretty sure that if you have a swapfile Ubuntu will attempt to use it

---

### Post by azad on 2007-10-18
I installed Ubuntu Fiesty on 30 PCs with 256 MB RAM. Works just fine.

---

### Post by JPWheless on 2007-10-18
With my PC, it freezes when i click on the installer icon. Everything else runs reeeaaaally slow.

Although, one time I left it like that for half an hour and it managed to get to the first screen.

---

### Post by louieb on 2007-10-18
Live CD + 256MB ram = Maybe (as you have found out)
The GParted live can create a swap partition. Make it a half gig or so. If you plan on dual booting windows be sure to  run the disk cleanup and defrag before shrinking the Win partition. 
Gparted can be found here. [SystemRescueCd]("http://www.sysresccd.org/Main_Page") or [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php")
and doc here [GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")
I prefer to use the System rescue CD when I use GParted.

---

### Post by jc_madden on 2007-10-18
I installed 7.04 on an old P3 w/ 256 ram, it was slow but it worked.  You might have a bad disc, have you tried using another copy?

---

### Post by JPWheless on 2007-10-18
Never mind, no more problems.

I figured out how to make a swap partition, and now the live CD and installer work perfectly.


Thanks for the help.

---

