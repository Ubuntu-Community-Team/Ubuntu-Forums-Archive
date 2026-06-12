---
title: "Hard Drive Troubles?"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by richuu on 2007-10-29
Due to messing around (er, I mean 'learning') with various installs of Ubuntu, I broke it a lot of times. Consequently, I've hard rebooted and re-installed a lot of times too. I think in the process, the hard drive has had a tough time of it. In my recent installs of Feisty Fawn (the only release that was really happy with my Wifi card), it kept hanging, mostly when I was downloading - a complete hang, nothing would get it out except 5 secs on the power button. 

I've just downloaded 7.10 and had trouble installing - the same hang I used to get with a fully installed FF, just stopping dead. I'm booted on the live 7.10 CD right now, and all is well. The CD checks out ok and the PC passes all memory tests. I've wiped all partitions off the HDD and want to give it a check, but it seems it won't check without partitions configured... is this the case? 

Either way, can someone give a complete noob a walkthrough of checking my HDD?

Many Thanks!

Rich.

---

### Post by 1337455 10534 on 2007-10-29
Well, i've only done it twice. Once on XP, (ill tell u how l8r) and once when Ubutnu said sda1 had been mounted 31 times without a check. Both checked the HDD for errors...
Look into md5summing your partition...
Wait, i am saying that you need to get Ubuntu / any Linux installed.. Then fish for HDD checking software.. Try SUSE 10.3 if u must.

---

### Post by richuu on 2007-10-30
Since I'm having trouble installing Ubuntu, is any other Linux going to be any easier?  Do I have any options such as partitioning the HDD (just one partition for the purposes of testing) and running fsck then? I might throw the drive into a Windows machine just to do the check.

---

### Post by richuu on 2007-11-07
Following on from this, I used Seagate's Seatools diag disk and did a full scan of the disk, and did a full low level erase of the disk. No errors showed at all. A further reinstall resulted in a lock up again.

Noticing in similar threads that nearly all used nVidia cards (and were having problems) I pulled the add in card out (Inno3D FX5500 256Mb) and relied on the onboard. I still get the same problem. 

It only appears to happen when I download anything... sustained downloads, I guess. It even fails on the Ubuntu updates.

---

