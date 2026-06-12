---
title: "Beginniner installation on Dell Inspiron 4100 - problem."
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by SpottydogWoodentop on 2008-03-12
Hi there:
First off, please forgive my lack of knowledge in the Unix field - I'm learning, and eager to know all - but I can't get past the first hurdle on my own!  I've downloaded Ubuntu 7.0 I downloaded Ubuntu 7.10 and burnt the iso onto a cd. I ran the cd from the disk drive onto the Dell Inspiron 4100 laptop I want to run it on. The laptop info (as far as I can tell) is Intel i845 chipeset, Pentium 4 (1595 Mhz) with 256 Mg RAM, 512 KB Cache, 20 gig harddrive, ATI Mobility graphics with16 MG SDRAM. The laptop had Windows XP already installed.

It ran (slowly) from the CD and looked ok – so I decided to go for it and install the Ubunto OS onto the laptop... and clicked on install on the desktop.  Eager to install it and start using a REAL operating system for a change.   Everything seemed to go ok – I entered all the requested info regarding time zones, etc.,  Ubuntu started the “Partitioner” BUT at 33% it just stopped altogether.  It never came back – I left it for over an hour with no joy whatsoever. The whole system was frozen.  So I did a hard shut down and retried. Now I can’t even get to that point in the installation, it just freezes after I select the time zone.

My question, (apart from the obvious “does anyone know what’s happening”) is – should I have formatted the hard drive and erased windows prior to clicking on the “install” button? My impression (from reading other thing) was that this install would just go over the windows xp system – write over it or something?  Also, if I DO manage to get the OS installed and running smoothly, will I be able to install something like Beryl, or XGL?

Btw, I had checked the CD and was told it was good – everything checked out.

The laptop, although somewhat old and dated, has been running more or less well, apart from the fact that it was running XP, and the CD Drive works fine, if somewhat slowly. 

any help / suggestions would be greatly appreciated.

Woof Woof. Spot.

---

### Post by Oldsoldier2003 on 2008-03-12
> **SpottydogWoodentop said:**
> Hi there:
First off, please forgive my lack of knowledge in the Unix field - I'm learning, and eager to know all - but I can't get past the first hurdle on my own!  I've downloaded Ubuntu 7.0 I downloaded Ubuntu 7.10 and burnt the iso onto a cd. I ran the cd from the disk drive onto the Dell Inspiron 4100 laptop I want to run it on. The laptop info (as far as I can tell) is Intel i845 chipeset, Pentium 4 (1595 Mhz) with 256 Mg RAM, 512 KB Cache, 20 gig harddrive, ATI Mobility graphics with16 MG SDRAM. The laptop had Windows XP already installed.

It ran (slowly) from the CD and looked ok – so I decided to go for it and install the Ubunto OS onto the laptop... and clicked on install on the desktop.  Eager to install it and start using a REAL operating system for a change.   Everything seemed to go ok – I entered all the requested info regarding time zones, etc.,  Ubuntu started the “Partitioner” BUT at 33% it just stopped altogether.  It never came back – I left it for over an hour with no joy whatsoever. The whole system was frozen.  So I did a hard shut down and retried. Now I can’t even get to that point in the installation, it just freezes after I select the time zone.

My question, (apart from the obvious “does anyone know what’s happening”) is – should I have formatted the hard drive and erased windows prior to clicking on the “install” button? My impression (from reading other thing) was that this install would just go over the windows xp system – write over it or something?  Also, if I DO manage to get the OS installed and running smoothly, will I be able to install something like Beryl, or XGL?

Btw, I had checked the CD and was told it was good – everything checked out.

The laptop, although somewhat old and dated, has been running more or less well, apart from the fact that it was running XP, and the CD Drive works fine, if somewhat slowly. 

any help / suggestions would be greatly appreciated.

Woof Woof. Spot.
considering the specs of the laptop i would consider using the alternate (text based installer) instead of the live CD to install.

---

### Post by Joeb454 on 2008-03-12
You could try using the alternate install CD, or possibly boot the current CD in Safe Graphics mode.

It could be te ATi Card causing issues (ATi & Linux don't always play nice :()

---

### Post by billgoldberg on 2008-03-12
How did you burn the disc?

Did you burn at the lowest possible speed? 

Burning cd's at a too high speeds can produce errors.

Try this guide for burning the iso and follow everything to the letter:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---------------

You might want to try the alternate cd (without a graphical installer, aka a text only installer (like windows xp home)).

---------------

Beryl is outdated, it's called compiz fusion now. It might run on your pc but I seriously doubt it. That ati mobility card is ancient.

-------------------

Besides that, I think that xubuntu would run better on such hardware specs. Ubuntu will run, but xubuntu will run alot better.

Xubuntu is less user friendly than ubuntu.

-------------------

You could format the hdd with the [gparted live cd]("http://gparted-livecd.tuxfamily.org/") before running the live cd or alternate cd, you  never know it works.

And gparted is a nice live cd to have laying around for emergencies.

-----------

Live cd's always run slow. It's because everything needs to be read from the cd instead of the hdd, which is allot faster.

---

### Post by NorthernLights on 2008-03-12
I second upper posts. I had the exact same problem with Kubuntu 7.10 on a 256 MB RAM machine and used alternate CD to install, with no problem.

---

