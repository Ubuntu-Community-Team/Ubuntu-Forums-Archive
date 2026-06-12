---
title: "Installation hangs at 15%,"
date: 2007-05-05
forum: Apple Intel Users
---

### Post by AutumnSkyline on 2007-05-05
I am installing Ubuntu 6.0.6 LTS on a Core 2 Duo iMac. On the 7.whatever version, the installation hangs at 50%, but on this, it stops at 15%: Detecting File Systems. What should I do?

---

### Post by AutumnSkyline on 2007-05-05
Okay, now it wont install anything at all. Should I just try to restart my computer and boot from the cd again??

---

### Post by AutumnSkyline on 2007-05-05
okay, so no thanks to anyone on the boards, I have figured it out. I don't think I will be coming here often.

---

### Post by tgalati4 on 2007-05-05
I just woke up.  You should wait at least an hour between posts.  I haven't even dug the crud out of my eyes.  Well, the forums have served their purpose.  They prompted you to fix the problem yourself.  

By the way, what fixed the installation?  There are probably others that could use the info.

Oh, and good morning.

---

### Post by Chrisj303 on 2007-05-05
> **AutumnSkyline said:**
> okay, so no thanks to anyone on the boards, I have figured it out. I don't think I will be coming here often.


Jesus christ - you didn't even wait an hour before deeming us useless!

Well good luck without us - this is definitley the best, most active board for apple-intel-ubuntu users.

---

### Post by AutumnSkyline on 2007-05-05
Sorry, Everyone. Iwas a liiitle peed. I'm used to getting quick replies at Macrumors.com and I saw the other threads getting replied to quickly. Now I hope you'll help me still:( :confused: . Basically, I tried it, and the GRUB or whatever wouldn't load, and I don't like running off of a live CD, so I want to get Mac OS X back. However, GPartition doesn't allow you to format in hfs+, and when I go to re-install OS X, it doesn't recognize the free space. What should I do? I did not use a bootcamp partition, because the last time I tried it, it wouldn't work...any ideas?

---

### Post by Slackpacker on 2007-05-05
Did you check out the [Macbook howto]("https://help.ubuntu.com/community/MacBook")?  You might have an easier time with Feisty, since it uses a more recent version of GRUB that can use the Boot Camp partition.

---

### Post by AutumnSkyline on 2007-05-05
Well, I don't have a Mac OS partition, it was deleted when I reformatted the drive :(

---

### Post by Chrisj303 on 2007-05-05
^So, you didn't read a guide - if you had then you wouldn't have had an issue with grub, the one linked above gives you cut/paste terminal commands to configure it.

---

### Post by tgalati4 on 2007-05-05
I am fully awake now.  What did I miss?

---

### Post by 87esir on 2007-11-11
I know this thread is old but I thought I would post my findings.

I tried to load ub7 several times and it hung on 15% and tried most everything I read except one about removing a certain video card that was causing it (mine didn't have that card so I know that wasn't causing my problems)

What I found was that it has something to do with the disc formatting process of my first partition (the one ub7 is going to).
What I did was use gparted to format that partition so it would be clean and then I tried to load. It still hangs on 15% but it will eventually load. The screen even gets strange at times and it may take 2 hours but it loads and it does work with the boot loader installing also. I tried it both ways and it worked twice now so it must have trouble formatting the disc and more so if there is a lot of info it has to format away.

When the screen does come back with movement and numbers it goes straight to formatting my second partition so it is definitely something to do with formatting my first. It has no prob. with the swap though. Then it loads the files just fine.

I don't know if this has anything to do with my drive or other hardware but if it interests anyone I am running a bone stock dell 4100 inspiron.

---

