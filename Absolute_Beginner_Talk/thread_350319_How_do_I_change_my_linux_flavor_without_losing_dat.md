---
title: "How do I change my linux flavor without losing data?"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by parmenides on 2007-01-31
I am currently running a debian install on a dual booting laptop, and I want to change to ubuntu, but I have all of my emails stored on the debian partitions. What do I need to be aware of when I upgrade so I don't lose them all? besides the obvious don't change the partitions....

---

### Post by Brunellus on 2007-01-31
many people report success by multibooting and sharing a /home partition--that is, having each distro have its own / but having all distros mount the same partition as /home

---

### Post by parmenides on 2007-01-31
so installing will not just update the os? it will modify everything?

---

### Post by Brunellus on 2007-01-31
> **parmenides said:**
> so installing will not just update the os? it will modify everything?
define "install" and 'update the os"

I'm talking about booting multiple distributions on a single machine.  each distribution gets its own partition for /, while they all share /home.  so imagine host examplebox:

/dev/hda1      is debian's /
/dev/hda2      is ubuntu's /
/dev/hda3     is /home   (for ALL DISTROS)
/dev/hda4    is  swap

---

### Post by parmenides on 2007-01-31
I dual boot with debian and windoze xp. I want to change the debian to ubuntu. Can I install the new over  the existing debian without sacrificing my data? Can it replace the debian, but NOT the existing information such as emails, documents and music files I have stored on it already?

---

### Post by lamego on 2007-01-31
To avoid this problem you should have created a dedicated /home partition, if didn't had this care on the first place you should now shrink your current partition, create a new /home for your data, and move it to your new partition.
Then you can safely do a fresh install, using your old / and your new /home to keep the data.

---

### Post by m.musashi on 2007-01-31
> **Brunellus said:**
> many people report success by multibooting and sharing a /home partition--that is, having each distro have its own / but having all distros mount the same partition as /home

I did this with dapper and edgy for a while but some things got pretty messed up. Data was fine but themes, panels, etc were totally hosed. It seems a lot of theme files are hidden in /home. There may be a way to make this work but I gave up and now use separate /homes but mount them all.

> **parmenides said:**
> I dual boot with debian and windoze xp. I want to change the debian to ubuntu. Can I install the new over  the existing debian without sacrificing my data? Can it replace the debian, but NOT the existing information such as emails, documents and music files I have stored on it already?

If you install ubuntu to the same partition as debian (in order to replace it) you will wipe out everything on that partition (unless there is a trick I'm unaware of). I believe the root partition will reformat automatically and you don't have the option to not format it (it's grayed out). Even if you could do it, I don't think you would want to. The best you can do is back up /home and anything else you don't want to lose and do a clean install. When you do the new install, put /home on its own partition and you will be set for any future reinstalls.

---

### Post by muguwmp67 on 2007-01-31
> **lamego said:**
> To avoid this problem you should have created a dedicated /home partition, if didn't had this care on the first place you should now shrink your current partition, create a new /home for your data, and move it to your new partition.
Then you can safely do a fresh install, using your old / and your new /home to keep the data.

I tried to create a separate /home partition the other day during an install,  but the current partitioner used by ubuntu makes setting up a separate /home partition really intimidating.

Its been a long time since I used it, but I remember fedora made it a lot easier.  One thing it did was allow you to modify the suggested partition configuration that it came up with.  In ubuntu, if you manually partition, you aren't given anything to start with.  A separate /home partition makes good sense, is there a way to report this to ubuntu development so they could make it easier?  A  checkbox that said 'create a separate /home partition' while partitioning would be very useful.

---

### Post by punx45 on 2007-01-31
whether the debian install is all on one partition or not, back up everything you think is important.   whenever a partitioner is run, no matter who is using it, no partition is invincible.

---

### Post by m.musashi on 2007-01-31
> **muguwmp67 said:**
> I tried to create a separate /home partition the other day during an install,  but the current partitioner used by ubuntu makes setting up a separate /home partition really intimidating.

Its been a long time since I used it, but I remember fedora made it a lot easier.  One thing it did was allow you to modify the suggested partition configuration that it came up with.  In ubuntu, if you manually partition, you aren't given anything to start with.  A separate /home partition makes good sense, is there a way to report this to ubuntu development so they could make it easier?  A  checkbox that said 'create a separate /home partition' while partitioning would be very useful.

This is very easy to do in Ubuntu. When you select manually partition, create the partitions you need (generally a /home, a / and a swap). I put them in that order so that swap is at the end but it may not matter). If you are unsure how to do the partitions I can explain that too but you seem knowledgeable. Once you have the three partitions (and everything is backed up that you don't want to lose) click next or continue and you will see the mount point set up. Set /home to whatever partition you want for that, / to the other and swap to swap. I tried to find a nice how to on this but didn't see one right off. I'm sure there is one out there. Here is a least one [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/) but it's not quite the same thing that you are doing.

---

### Post by muguwmp67 on 2007-01-31
Okay, so I tried the install again, this time with manual partitioning.  It wasn't as painful as it looked.  I've done partitioning in Windows before, but the choices seemed more complicated at first glance.

What was REALLY interesting was that a side effect of the manual partitioning is that Ubuntu mounted my other NTFS drives during the install.  It didn't do this when I did a reformat and partition on the drive.

---

### Post by macogw on 2007-01-31
I have Feisty, Fedora, Sabayon, and Edgy all multibooting with a shared /home.  Setting that up, as long as they are of the same line (Ubuntu comes from Debian, so that counts) is simple.  Mixing RH, Gentoo, and Debian required tinkering (different group numbers--Deb starts at 1000, RH at 500, and Gentoo puts 1000 for user and 100 for group), but it mostly works now.  Fedora just puts OOo in the menu twice because it sees the path Deb-based distros use (meaning the 2 Ubuntus) and has OOo in a different one, so it shows both.  That's about it.

---

