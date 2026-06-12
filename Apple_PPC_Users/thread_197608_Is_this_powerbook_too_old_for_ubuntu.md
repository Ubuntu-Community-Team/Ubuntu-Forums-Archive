---
title: "Is this powerbook too old for ubuntu?"
date: 2006-06-16
forum: Apple PPC Users
---

### Post by rittub on 2006-06-16
Hi, recently I got an old powerbook with a 400mhz CPU, 64MB of ram and a 5G hard drive. I wonder if it too old for ubuntu...
I simply don't like OS 9 and would like to intall linux on it, if it is too old for ubuntu, could anyone recommend a linux distro? Thanks. :confused:

---

### Post by johnc4510 on 2006-06-16
XUbuntu might work, if not try Dam Small.

---

### Post by glotz on 2006-06-16
(Definitely no chance of running gnome.)

---

### Post by IYY on 2006-06-16
Won't run Gnome, but IceWM or Fluxbox will run very well.

---

### Post by uros678 on 2006-06-16
I think you need to upgrade the amount of ram you have in the computer, but it's still not going to "go" very fast.. :) But it can be done at least.. ubuntu with gnome that is... maybe if you try some more lightweight windows managers...

best regards,
uros

---

### Post by void_false on 2006-06-16
I wish I had your laptop ;)

---

### Post by Ububurns on 2006-06-16
No, I don't think it's too old.

Ubuntu is running comfortably with my 466MHz Mac.

But yes, you will need more memory to run Gnome, comfortably.  There are other alternative attractive and functional desktop managers / window managers one can install and use in Ubuntu, including (as previously mentioned) XFCE, Enlightenment, IceWM etc.

---

### Post by miahfost on 2006-06-16
You will want to check carefully your chip architecture. Some older PowerPCs do not accept linux at all. I think though, due to the amount of disk space you have, that yours should be ok.

---

### Post by AlphaMack on 2006-06-16
I have a 300 MHz G3 iBook running Ubuntu Breezy with 288 MB RAM (originally shipped with Mac OS 9.0.2).  You definitely will want to upgrade your RAM - max it out if you can especially since it's so cheap.

---

### Post by warp99 on 2006-06-16
[QUOTE=rittub]Hi, recently I got an old powerbook with a 400mhz CPU, 64MB of ram and a 5G hard drive. I wonder if it too old for ubuntu...
I simply don't like OS 9 and would like to intall linux on it, if it is too old for ubuntu, could anyone recommend a linux distro? Thanks. :confused:[/QUOTE]

I have an original clamshell G3 366mhz with 512mb ram and everything runs great under Dapper. The only problem was the kernel issue which was resolved as of today. I did upgrade today and everything is running pretty good except the Java plugin doesn't work under firefox 1.5 in the repos. 

I can tell you that Dapper runs FASTER than Breezy on this particular machine. One thing I did is use ReiserFS with notail and noatime enabled in fstab. It seems to make a BIG difference in load times. I going to start blacklisting some of the modules not used so everything will load a little faster. :cool:

Edit: The clamshell is a 300mhz with an additional 512mb of ram for a total of 544mb. You may want to upgrade the hard drive and the CDR. The CDR that was in the clamshell would not read any of the discs I burned, so I just upgraded to a CDR-DVD.

---

### Post by AlphaMack on 2006-06-17
I'm still unsure as to whether it's safe to dist-upgrade from Breezy as the kernel bug in the original Dapper final release was the reason why I settled for Breezy instead on that Clamshell.  Has there been any mention of the possibility of respinning Dapper?

---

### Post by glotz on 2006-06-17
What kernel bug do you refer to?

---

### Post by blkish on 2006-06-17
[QUOTE=rittub]Hi, recently I got an old powerbook with a 400mhz CPU, 64MB of ram and a 5G hard drive. I wonder if it too old for ubuntu...
I simply don't like OS 9 and would like to intall linux on it, if it is too old for ubuntu, could anyone recommend a linux distro? Thanks. :confused:[/QUOTE]

you might like to look into a project called 'ubuntulite' which i believe is aimed at ubuntu on lower-spec computers.

i'm not sure if they support ppc though.

good luck!

blkish

---

