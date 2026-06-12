---
title: "Ubuntu slowing down???"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by bagrol1 on 2007-06-20
I'm a new Ubuntu user... noticed that after a few days after fresh install and adding several programs, Ubuntu launches progs a little slower than in the beginning.  This reminds me of Windows XP which gets constantly slower with time.

Any of you noticed a slowdown in Ubuntu over time????

I've actually built a new computer to be able to run Ubuntu (E6420 C2D overclocked to 3.5GHz, 2GB RAM, NVIDIA 7900GS, Seagate 320GB HD).  I have XP on older Maxtor HD and Ubuntu on new Seagate (dual boot).  Now after a few days of use I think that Ubuntu is not faster than XP _solely based on application launch time_ (OS boot time seems to be about the same or even slower for Ubuntu as I have to enter the password).

And if I look deeper Ubuntu has a brand new and quicker HD (Seagate 7200.10 16MB cache) and even this advantage seems to be already gone (XP is on 4 y.o. 160GB Maxtor).

Any thoughts/experience????

---

### Post by king0lag on 2007-06-20
I'm having this issue too, someone suggested it could be my video card but I switched to unsupported drivers long ago and have been running with no problem in regards to that. Is there a quick mantainince guide for ubuntu out there? Hmmm

---

### Post by phr0ze on 2007-06-20
What programs have you added? Skype, GAIM, Beryl, etc?

Let us know.

---

### Post by diatribe on 2007-06-20
I've not encountered this problem

---

### Post by Tyke91 on 2007-06-20
me niether, my ubuntu is pretty much as fast as it was in the first week.

---

### Post by bagrol1 on 2007-06-20
Added Beryl, Thunderbird, crossover office, and bunch of smaller apps. 

Most importantly had to remove and install Beryl a few times to get things to work, the same about Nvidia drivers.  Just wonder if there are a lot of "leftovers" in the system.

PLUS I don't have any virus scan in Ubuntu which should be another speed advantage over XP.

---

### Post by king0lag on 2007-06-20
> **bagrol1 said:**
> Added Beryl, Thunderbird, crossover office, and bunch of smaller apps. 

Most importantly had to remove and install Beryl a few times to get things to work, the same about Nvidia drivers.  Just wonder if there are a lot of "leftovers" in the system.

PLUS I don't have any virus scan in Ubuntu which should be another speed advantage over XP.

I just read this post [http://ubuntuforums.org/showthread.php?t=478691](http://ubuntuforums.org/showthread.php?t=478691) which helped alot, but I'm still draggin. I mean when I installed Ubuntu it was FLYING!!!! The only applications I can recall installing were the Amarok player, and VLC but I'll have to check... I know that everything I have installed has been through the package manager except for wine perhaps...

---

### Post by ECPCLINUX on 2007-06-21
My problem is that after almost 7 month  of Ubuntu 6.10 on my Intel Mobo 865 Chipset, CPU Intel 805 over clocked  @ 3.0 with 3GB ddr2 667 and one 250 sata Western Digital HD, that it takes forever to boot. Once I boots up all is well and Ubuntu seems to run just as fast as it did the first day I installed it. As a matter of fact I don't think, at least I don't notice, an improvement in performance when I added an extra Gig of ram. As some one mentioned the only application/program that was, is and seem it will always be slow is Amarok. Like others here I have installed too many programs and games to remember them all, maybe that's the problem,lol;).  Ubuntu does a forced check when booting every once in a while but it solves nothing nor does it seem to find anything wrong. Until I saw this link I had not mentioned anything an lived with it, by keeping my Box on most of the time. If there is a check I could do to improve my boot up time would someone please post it here?  Perhaps at boot up something could be checked or done or using a Terminal. I would appreciate any help comments as well.  I just Installed Ubuntu 7.04 in a  smaller Computer and it boots faster. Ahead of time I like to thank anyone who might help here.

---

### Post by arvevans on 2007-06-21
I turned off (uninstalled) all the bluetooth stuff.  I don't use it anyway.  That made a noticeable difference in application loading.  Still not great, but better than before.
_._

---

### Post by Hobo Joe on 2007-06-21
Everything loads fine for me, but I have noticed that the login time is slower. To make that clear, the loading point AFTER the OS has booted, when I am loggin into my username.

When I first installed it started up super fast.

---

### Post by maddot on 2007-06-21
hmm..try going into session, under settings... it's in either one of the menus. Look see if there is any particular one that you think is causing the long boot time.

Also, beryl is known to produce a lag in some pcs. Not all.... But it could be the cause of your problem?

---

### Post by Hobo Joe on 2007-06-21
I doubt that would be it. I've checked sessions, and the only thing that has been added is Beryl.

But considering I have a 5200+ and an 8800 GTS (yeah, I really do :D)I don't think that's the source of the problem.

---

### Post by Mazehero55 on 2007-06-29
here you go! This is a howto to speed it up. 

[http://yoten.blogspot.com/2007/04/speed-up-ubuntu.html](http://yoten.blogspot.com/2007/04/speed-up-ubuntu.html)

[Edit] by the way, adding the profile thing in menu.lst, I found to actually make my boot alot slower. if your boot is slower after this then try get undoing this.

---

### Post by HotShotDJ on 2007-06-29
Did you by any chance install beagle without first enabling extended attributes for the file system?

---

