---
title: "xbuntu installing problems"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by Th3Futur3 on 2006-08-17
Hi, I burned xubuntu on iso disk and the live cd works fine. When I click install on the desktop it goes fine till i gets to step 5 which is partioning the hard drive. It shows it load to 100% but then nothing comes up. It went like that for 2hours. I checked the cd for defects and everything checked out ok. What am i supposed to do.

BTW the pc im installing it on is pretty old. It only has 128mb ram
and a 15gb hardrive. The processor is an old AMD Athlon.

---

### Post by sean_ on 2006-08-17
Try re-burning your CD. Also, I suggest not having them both installed at the same time unless you'd like each OS to be under 10 GB.

---

### Post by Th3Futur3 on 2006-08-17
Ok...how can i fully uninstall windows...can i use the disk?

---

### Post by lyleogle on 2006-08-17
Same on a DELL PIII @ 450mhz ! Tried many times with no luck, these were Ubuntu supplied CD's

---

### Post by PHuN on 2007-08-23
I know this post is a little old but I figured it was the best header for what I am/ran into.

I am trying to install xbuntu on a 500mhz x86 512mb mem with junk everything else (bios is from '98) Just want nice little system to run LAMP on with a couple extra services.

I ran into an issue with the two hard drives that were in it 10gb, 3.5gb.
When I booted live cd both hdd's were on the desktop as "disks" with gb labels respectively (I believe that is right).

I would get to the part of creating partitions, I would try to install OS on the 3gb drive but kept coming up with errors of "partition failed on hda".
OK...try hdb for root...nope "partition failed on hdb"

There was an install of ubuntu on the 3gb, but decided after reading some that xbuntu would serve me better (ubuntu was way too sluggish running gdm, heard xfce was much better for slower systems)

But try as I might I couldn't fdisk, parted, gparted to clean everything away.
I knew the hdd's were not defective, had 98 on both not too long ago.
It seemed that I couldn't "wipe and clean" the drives because while in live cd you don't have enough privileges to do so. (I think)

Out comes Win XP pro cd, it doesn't care at all, "You wanna format that hdd, SURE!!!, and that one too??? - WHY NOT, let's do it!!!"

Just incase I run into installing either xbuntu, or ubuntu - is there anything that I can do through linux to accomplish this, next time I may not have the handy "CLEANER DISC"???

I would really like to know if you have any input,

Thanks,
-PHuN-

(ps - as of right now I believe xbuntu is installing on that computer right now, not sure how far along it is as I am writing this.  I do know that the 3gb will still need work as it still showed up as having errors (I guess) and I couldn't install to it, I will use it as a small ext partition for storage, not wat I really wanted - oh well)

---

### Post by hyper_ch on 2007-08-23
For installtion the alternate cd is recommened...

Upon booting you have for either cd also the option of checking it for defects. Maybe there is one.

---

### Post by PHuN on 2007-08-23
I was thinking about trying out the alternate install but opted to go with the live cd, will definitely do that next time, alternate that is.

As for the defect possibility, I checked the cd twice (albeit after running into the problems), both on my laptop (MD5), and on the computer that I installed it on (CD check), both times came out okie dokie. (not sure if they are one in the same)

Thank you.

---

### Post by PHuN on 2007-08-23
one more thing, do you have any advice on how to clear up the issue with the 3gp hdd.  I know there could be a myrad of possiblities, but let's assume (yes, assume) that the hard drive is in good order, what should I do to make it operational?

---

### Post by hyper_ch on 2007-08-23
well, if you booted into ubuntu and try gparted or any other program from there it won't work as you will have the 3gb hdd mounted... you can delete it with the installer cd :)

---

### Post by LowSky on 2007-08-23
try Damn small linux it will run on old 486 computers

or puppy if you want something a little more zesty

---

### Post by Tyke91 on 2007-08-23
Damn small linux is a nice find... made my grandpas 15 year old computer run like a constapated wiener dog (in other words.... really fast)


try burning the xubuntu install cd on the LOWEST speed possible (usually x8 but the best would be x1)

---

