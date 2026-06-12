---
title: "64 Bit Ubuntu vs 32 Bit"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by chperry on 2008-03-22
Last week I installed Ubuntu (or any Linux for that matter) for the first time on a P4 Dell.  It was the 32 bit version.  The installation went well for the most part.  Other than a few quirks with sound support and playing DVDs, the machine runs great.  It dual boots XP Pro and Ubuntu.

It went so well that when my new Dell dual core machine arrived on Thursday, I downloaded the 64 bit version of Ubuntu and installed it (again dual boot with XP Pro).  I am having some problems with Grub (if the hard drive is not the first boot disk in the bios, then grub does not load, I get a black screen) but otherwise it is doing well.

I picked up the book "A Practical Guide to Ubuntu Linux".  There is a single blurb about 64 bit linux saying you might want to consider using 32bit on 64 bit machines.  Why?  Have I made a mistake installing the 64 bit version?  Should I reinstall Ubuntu, but use the 32 bit version?

Thanks

Charles
BTW, Love Linux.  Fast and Gnome looks great.

---

### Post by zvacet on 2008-03-23
> if the hard drive is not the first boot disk in the bios, then grub does not load, I get a black screen

So let hard drive be first boot in the bios.

> Have I made a mistake installing the 64 bit version?

No you didn´&#359;.It is just that 64 bit have less support then 32 bit,but you have 64 bit subforum if you have any problem.If you don´t have more then 4GB of ram you can run 32 bit version(you can run it if you have more then 4GB but in that case you will not use all ram).In short,you can run both verions but in 32 bit version some thing are easyer to install(java,flash...).

---

### Post by jordank on 2008-03-23
In all honesty, unless you're doing something that is going to require a lot of machine thinking, 64 bit is most likely useless for you.  If you haven't done much with your setup yet, I can almost promise you that 32 bit would make your life a lot less stressful, and save you a lot of grief.  IMO.

---

### Post by chperry on 2008-03-23
I think I will opt for the 32 bit version then.  I currently have 2GB of ram and plan to add 2 more, so the 32bit should be fine.  Do I need to do anything special? Or just boot from the 32bit live CD and do an install on the existing partitions?

Thanks

---

### Post by ByteJuggler on 2008-03-23
Actually, not wanting to cause controversy, but running 64-bit these days is not as much of a challenge anymore as it once was.  Furthermore, if you're going to be running with 4GB, then you should ideally run a 64-bit OS - a 32-bit OS will be able to use at most about 3.2-3.5GB of RAM.  (So you'll "lose" about half a gigabyte to 3/4GB if you run 32-bit with 4GB RAM installed.)

I would in reality suggest you give your 64-bit install a damn good run through and see if there's anything in particular that doesn't work for you, and if you do find things that are problematic, then you've got a good reason to possibly run 32-bit.  If you don't, then I'd say stick with 64-bit.

---

### Post by Joeb454 on 2008-03-23
If you're not in a hurry, then install Ubuntu 8.04 64 bit :)

I've had absolutely no issues with it :) It even uses nspluginwrapper to install Flash through ubuntu-restricted-extras

It's only a month so there's not long to wait

---

