---
title: "Dual Boot Question?"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by oroco on 2007-01-17
Hello. I have installed Ubuntu on  40 GB partition of the hard disk , now I intend to install XP. But some people say that I might get some problem related to GRUB. For this reason they advice me to remove Ubuntu , then install Xp as first. But I dont want to delete my Ubuntu box and I wish to install xp if it is OK. Do you recommend?

---

### Post by oyvindaa on 2007-01-17
I've never done it that way myself but I think you've to reinstall GRUB when installing Ubuntu before Windows.

See [this](http://ubuntuforums.org/showthread.php?t=24113&highlight=HOWTO+GRUB).

Good luck :)

---

### Post by old_geekster on 2007-01-17
> **oroco said:**
> Hello. I have installed Ubuntu on  40 GB partition of the hard disk , now I intend to install XP. But some people say that I might get some problem related to GRUB. For this reason they advice me to remove Ubuntu , then install Xp as first. But I dont want to delete my Ubuntu box and I wish to install xp if it is OK. Do you recommend?
Since you just installed Ubuntu, you shouldn't have much time invested.  The reason I mention this is, it is far better, actually recommended, to install Windows first.  I believe the main reason for this is because Linux recognizes Windows partitions, but Windows doesn't recognize Linux partitons.  The out-come may be less that the best if you install Ubuntu first.  Truthfully, I don't know if you can do it that way.  I wouldn't! 

I have done the duat-boot setup on a siingle drive numerous times; SuSE 10 & Ubuntu.  Installing Linux over Windows is very easy.  I highly suggest using the "Manual Partitioning" feature.  Windows will be on partition sda.  Ubuntu will be installed on sdb.

When you install Windows, be sure to leave half of the drive as "Free Space".  This makes it easier for Ubuntu, and less trying for you, to install.

p.s. A 40GB drive is small for two OS'es, but it will work.  You simply don't have much room for programs; especially games.  I prefer at least 80GB's.

Update:  I have been doing some further research.  It appears there is a partitioning program for Linux called "GParted".  You can use it to partition your drive with Ubuntu installed.  Then, you can install Windows.  Would I use it, no.  Why, because I am new enough to this OS that I want everything straight forward.   I may use it later, if I find it necessary to have more room for the OS.

---

### Post by oroco on 2007-01-17
Thanks @old_geekster  , I will care your advice.

---

