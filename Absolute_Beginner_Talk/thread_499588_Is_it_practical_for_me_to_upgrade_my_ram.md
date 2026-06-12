---
title: "Is it practical for me to upgrade my ram?"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-07-12
I have a relatively cheap modern laptop laptop that I bought a year ago. It is the BenQ R31E. It has a 60 GB hard drive, 512 MB ram, generic intel video card, etc. I run Kubuntu Feisty on it. I want speed, but I prefer KDE over Xubuntu because I fell in love with KDE.

I am the type of user who loves to run lots of applications (Kopete, Adept, KTorrent, Amarok, Kerry, Konqueror, Opera, Kontact, and some other little apps run in my ordinary sessions), but sometimes, my relatively cheap modern laptop can't handle running all those applications and it slows down or freezes if there are too many processes.

I am thinking of upgrading my 512 MB ram to 1GB. Do you think it is advisable? Also, if I upgrade, is 1GB of ram the right size?

:KS

---

### Post by greg_g on 2007-07-12
Yes it is practical, and the right size is however much you can afford really.  I mean, any more than 1 gig and you start to hit the "diminishing returns" problem, but 1 to 1.5 would be the sweet spot probably.

---

### Post by Gen2ly on 2007-07-12
> **wersdaluv said:**
> I have a relatively cheap modern laptop laptop that I bought a year ago. It is the BenQ R31E. It has a 60 GB hard drive, 512 MB ram, generic intel video card, etc. I run Kubuntu Feisty on it. I want speed, but I prefer KDE over Xubuntu because I fell in love with KDE.

I am the type of user who loves to run lots of applications (Kopete, Adept, KTorrent, Amarok, Kerry, Konqueror, Opera, Kontact, and some other little apps run in my ordinary sessions), but sometimes, my relatively cheap modern laptop can't handle running all those applications and it slows down or freezes if there are too many processes.

I am thinking of upgrading my 512 MB ram to 1GB. Do you think it is advisable? Also, if I upgrade, is 1GB of ram the right size?

:KS

I not sure if this will help but... I use gnome and started with 512MB of RAM when I used OS X.  It wasn't near what I needed!  So I bought a 1GB board of memory.  Since I've moved to gnome I've never used more that 512MB!  It's frustrating because 1GB then costed me 120-130 dollars at Staples.  You can probably get it cheaper now.  I think KDE requires larger amounts of memory however, and when you begin paging in and out a lot you computer starts to drag.

---

### Post by scragar on 2007-07-12
try searching the forums for "fiesty freezes" first, there appear to be many threads about it, and I myself experience fiesty freezing with only 1 or 2 programs open(2 system applications consume 47% of my CPU each and cause everything to freeze) around every 25 minutes.

---

### Post by Rocket2DMn on 2007-07-12
If you think it might not be a RAM problem you can follow scragar's advice, but it sounds like a RAM shortage to me.  I've noticed that Xorg starts eating up more RAM as time passes, so you can check that too.  A GB of RAM should be enough, but 1.5 is OK if you think you will use it.
I see a RAM upgrade in your near future...

---

### Post by jrusso2 on 2007-07-12
buy another 512 stick you should have another open slot and that should give you enough ram.  512 mb ram sticks are not like $60

---

### Post by wersdaluv on 2007-07-12
Let's suppose that I decide to upgrade my RAM. After the upgrade, will I have to do special configuration or whatever, or would the RAM not affect my software?

---

### Post by Rocket2DMn on 2007-07-12
Your motherboard and BIOS will detect the addition, Kubuntu shouldn't give you any trouble.  Just make sure you get the correct type of RAM to match what you currently use.

---

### Post by davidsrsb on 2007-07-12
Ubuntu does not need any configuration to use extra ram.

Your swap may then be undersized, but that only matters for hibernate/suspend.

---

### Post by greg_g on 2007-07-12
I will post again to make Rocket2DMn's point solid.  Make ABSOLUTELY SURE you get the right RAM.  A lot of issues come from wrong RAM and sometimes the process of returning it for a refund or whatever is a pain.

Your manufacturer should have a list of compatible RAM, and hopefully with the specs they are looking for (CAS latency and such, I don't know what they mean, but you want the numbers to match ;) )

---

### Post by Gen2ly on 2007-07-13
> **greg_g said:**
> I will post again to make Rocket2DMn's point solid.  Make ABSOLUTELY SURE you get the right RAM.  A lot of issues come from wrong RAM and sometimes the process of returning it for a refund or whatever is a pain.

Your manufacturer should have a list of compatible RAM, and hopefully with the specs they are looking for (CAS latency and such, I don't know what they mean, but you want the numbers to match ;) )
!
> **Rocket2DMn said:**
> If you think it might not be a RAM problem you can follow scragar's advice, but it sounds like a RAM shortage to me.  I've noticed that Xorg starts eating up more RAM as time passes...[FONT="Fixedsys"]Hmm this should not happen.  I've run x for days and and haven't seen this.[/FONT]

---

### Post by wildseven on 2007-07-13
Make sure to resize your Swap Partition. Use Qtparted or other such programs. And don't make the swap bigger than what you have left for space otherwise you will get a dump error.

---

### Post by rfurman24 on 2007-07-13
You will not need to resize your swap. Swap is only used when ram runs out. With more ran you will need less swap but you will not need to resize.

---

### Post by laidback on 2007-07-13
I use Crucial ram, their site will help you find the correct ram. I've done it with 3 different computers, 2 desktops and 1 laptop. So far I've had 100% success. Google for Crucial ram and follow the instructions, the site can even interrogate your machine if you want it to.

---

### Post by wersdaluv on 2007-07-14
I already have 2GB allocated for swap even if my ram is only 512 MB

---

### Post by ramjet_1953 on 2007-07-14
Another aspect is that Linux uses RAM for cache, when applications don't need it. 

I have 1.25Gb of RAM and at this moment I am only using 33% of it for applications, and 66% as cache.

What this means, is that my system virtually never needs to use the swapfile.

This is good, as it means my system will operate faster.

Regards,
Roger :cool:

---

### Post by macogw on 2007-07-14
> **Dirk.R.Gently said:**
> !
[FONT="Fixedsys"]Hmm this should not happen.  I've run x for days and and haven't seen this.[/FONT]

If you use Beryl, it happens more, especially if you use AIGLX because AIGLX does all the processing in Xorg (or some explanation along those lines).

The CAS Latency does not have to be the same.  The speed has to be the same.  The lower the CAS Latency is, the better your system will run.  There are 2 numbers you want to look for, the type and the speed.  My laptop uses DDR2 (that's the type) PC2-4200 (which believe means 4200MHz, the PC2 may actually be referring DDR2 as well, but I don't know).  One of my desktops uses DDR PC-2400, and a few others use SDRAM PC-100 (meaning 100MHz) or PC-133 (133MHz).  Sometimes it's ok for the clock speed to be a bit off.  For instance, I have PC-100 in a computer than can take PC-133 and in one that should use 66MHz RAM.  The 133MHz one is slowed down a bit by having slower memory in it, but it won't damage anything.  The 66MHz one is able to scale the 100MHz memory I put in it just fine, but this isn't the case with all motherboards, so be careful (I only knew mine could do it because the previous owners put in 100MHz and it survived at least 5 years longer than that).

---

### Post by macogw on 2007-07-14
> **rfurman24 said:**
> You will not need to resize your swap. Swap is only used when ram runs out. With more ran you will need less swap but you will not need to resize.

Swap is usually 2x the amount of RAM you have.  It's not necessary that it be that size for the system to run, but if you hibernate, it goes there, and then you do need 2x that size.  However, you can trick it.  You could have no swap and then use a ramdisk so that it suspends/hibernates to the RAM instead of to a swap partition on the hard drive.  Now, I could certainly be wrong, but that's what I gathered (or inferred) on #ubuntu when I asked if it was really necessary for me to have the guy make a 4GB swap partition.

---

### Post by tgalati4 on 2007-07-14
Don't forget that KDE may get wonky with too many applications at once.  It's a known issue.  Go back to Gnome or XFCE if KDE dumps even with the extra RAM.

Only your hands-on experience will tell how well the extra RAM works.

---

### Post by wersdaluv on 2007-07-14
Another reason why I am thinking of a RAM upgrade is because I am looking forward to using KDE 4 on this laptop. Perhaps, the upgrade would help.

---

### Post by dorath on 2007-07-14
Before purchasing more RAM, be absolutely certain that you have a free slot avaliable to put it in.  You may only have two slots, and each slot might have a 256MB stick in it already.

As a side note, that Intel video card is probably stealing some of your existing 512MB.  That's called 'shared memory', and if that's what you have then you can probably vary the amount shared somewhere in the BIOS.  If you're not doing any 3D stuff (Compiz, games, etc) you can try reducing the amount of RAM the video card uses as a temporary reprieve until you can score more RAM.  If that causes problems, you can always reset it to the original value.

-dorath

> **wersdaluv said:**
> I have a relatively cheap modern laptop laptop that I bought a year ago. It is the BenQ R31E. It has a 60 GB hard drive, 512 MB ram, generic intel video card, etc.

---

### Post by swoll1980 on 2007-07-14
> **wersdaluv said:**
> I have a relatively cheap modern laptop laptop that I bought a year ago. It is the BenQ R31E. It has a 60 GB hard drive, 512 MB ram, generic intel video card, etc. I run Kubuntu Feisty on it. I want speed, but I prefer KDE over Xubuntu because I fell in love with KDE.

I am the type of user who loves to run lots of applications (Kopete, Adept, KTorrent, Amarok, Kerry, Konqueror, Opera, Kontact, and some other little apps run in my ordinary sessions), but sometimes, my relatively cheap modern laptop can't handle running all those applications and it slows down or freezes if there are too many processes.

I am thinking of upgrading my 512 MB ram to 1GB. Do you think it is advisable? Also, if I upgrade, is 1GB of ram the right size?

:KS

I started with 256mb in kubuntu. I upgraded to 768mb, I have not seen my swap being used once yet. The most I have seen being used is a tad over 700mb, and been like 3 weeks now, but I want to run a vm so I could defiantly use that extra 256mb

---

