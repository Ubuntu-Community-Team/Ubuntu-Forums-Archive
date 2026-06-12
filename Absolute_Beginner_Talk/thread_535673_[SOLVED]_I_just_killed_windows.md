---
title: "[SOLVED] I just killed windows"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by airbornemist6 on 2007-08-26
I just installed gfxboot, and I thought I had it working and then I tried loading files from my windows xp partition in linux... it said nothing was there and it couldn't mount it. well that seemed bad but i figured i just did something wrong and needed to boot into windows to get it to fix itself. Oh no! I was wrong! Instead, I chose to boot into windows and guess what! Grub pops back up. Now I think about it, when I did the install grub thing with gfxboot, i told it to install on sda1... which is my ntfs partition. did i just totally corrupt my partition... PLEASE TELL ME I DIDN'T! T.T

EDIT:

Ok I fixed it, I ran test disk ([http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)) off of a RIPLinux livecd. I just overwrote the MBR from backup, and repaired the MFT and now it works. not only that i can boot into windows again. really the trick i think is that you actually need to do this before even thinking about troubleshooting, otherwise you'll screw it up. oh and i also managed to keep my cool grub! w00t!

---

### Post by wolfger on 2007-08-26
I'm not positive, but I think you just fubared your windows partition. If you installed grub on sda1, then you can see sda1 by looking at /boot (in a term window, in Nautilus, in Konqueror, however). But I'm thinking grub can't exist on NTFS... and Windows won't exist on ext2.

---

### Post by sdowney717 on 2007-08-26
if it is XP, then you could try booting the XP install CD, get to recovery console and type FIXMBR
this will rewrtite the MBR of the windows partition and may be it will be fixed.

---

### Post by airbornemist6 on 2007-08-26
basically, i just had the same problem this guy had...

[http://ubuntuforums.org/showthread.php?t=410673&highlight=gfxboot](http://ubuntuforums.org/showthread.php?t=410673&highlight=gfxboot)

i don't know if he ever got it fixed, right now i'm just worried that i'll have lost all my info. oh god. i'm so screwed if i did.

---

### Post by dualsub2006 on 2007-08-26
> **airbornemist6 said:**
> basically, i just had the same problem this guy had...

[http://ubuntuforums.org/showthread.php?t=410673&highlight=gfxboot](http://ubuntuforums.org/showthread.php?t=410673&highlight=gfxboot)

i don't know if he ever got it fixed, right now i'm just worried that i'll have lost all my info. oh god. i'm so screwed if i did.

I am totally new to Linux. I have installed Suse a few times in the past but just for giggles. I never really had an interest in using it beyond just playing around. I have committed to making my general office and email machine Linux so I put Ubuntu on an old Dell laptop to avoid having to buy new.

 I always installed Suse on a machine solo and I did the same thing with Ubuntu. There is simply too much to risk by trying to set up a dual boot machine that I just never wanted to chance it. I have back ups of all of my Windows data, but the thought of whacking my WinXP or Mac OS X drive in a mistake is too much for me to handle.

I hope you guys are able to rescue your business, but learn from it in either case.

---

### Post by airbornemist6 on 2007-08-26
> **dualsub2006 said:**
> I am totally new to Linux. I have installed Suse a few times in the past but just for giggles. I never really had an interest in using it beyond just playing around. I have committed to making my general office and email machine Linux so I put Ubuntu on an old Dell laptop to avoid having to buy new.

 I always installed Suse on a machine solo and I did the same thing with Ubuntu. There is simply too much to risk by trying to set up a dual boot machine that I just never wanted to chance it. I have back ups of all of my Windows data, but the thought of whacking my WinXP or Mac OS X drive in a mistake is too much for me to handle.

I hope you guys are able to rescue your business, but learn from it in either case.

well actually, i'm using ubuntu. and dualboot systems are extremely safe, the problem comes when you decide to mess with grub. and when grub is willing to do things it's not supposed to do.

---

### Post by Skidpad on 2007-08-26
> **airbornemist6 said:**
> well actually, i'm using ubuntu. and dualboot systems are extremely safe, the problem comes when you decide to mess with grub. and when grub is willing to do things it's not supposed to do.
Since you are running Ubuntu, can you see your Windows partition and access your data?

---

### Post by airbornemist6 on 2007-08-26
> **Skidpad said:**
> Since you are running Ubuntu, can you see your Windows partition and access your data?
i wish. i see the partition and it supposedly recognizes it as ntfs, but in gparted if i right click and click properties it says it can't read it and might need to install the correct plugin. oh man i'm going to cry if i can't fix this.

---

