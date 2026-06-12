---
title: "Building (my first) computer, a few questions"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by gohome190 on 2007-11-01
Hey.  New here, and with Ubuntu.

1.  Will I be able to run the newest Ubuntu, Gutsy, with these base specs?

MotherBoard-ASUS M2NBP-VM CSM (socket AM2; Nvidia Quadro NVS 210S/ Nforce 430B)

CPU-AMD Athlon 64 3200+

Memory-Corsair XMS2 1GB DDR2-800

2.  Is Gutsy recommended for newbies, or should I go with Dapper, the latest LTS?

3.  Say later on down the road I want to install say Windows XP.  Can I do this without harming any files?  Can I keep both Ubunutu and XP?

Thanks in advance.

---

### Post by oilchangeguy on 2007-11-01
> **gohome190 said:**
> Hey.  New here, and with Ubuntu.

1.  Will I be able to run the newest Ubuntu, Gutsy, with these base specs?

MotherBoard-ASUS M2NBP-VM CSM (socket AM2; Nvidia Quadro NVS 210S/ Nforce 430B)

CPU-AMD Athlon 64 3200+

Memory-Corsair XMS2 1GB DDR2-800

2.  Is Gutsy recommended for newbies, or should I go with Dapper, the latest LTS?

3.  Say later on down the road I want to install say Windows XP.  Can I do this without harming any files?  Can I keep both Ubunutu and XP?

Thanks in advance.



1. you should have no problem running 7.10 with your computer.

2. 7.10 is fine for newbies. just be aware, there have been many problems posted here in the forum. most were probably caused by upgrading 7.04 to 7.10. it's always best to do a clean install, of any os.

3. your best bet would be to install windows first, then ubuntu. windows boot record will overwrite ubuntu's, if installed second (you will have to reinstall grub). and always back up your files just incase something goes wrong.

---

### Post by cyclefiend2000 on 2007-11-01
to add to what is said above, i would make a separate partition for /home so if the OS crashes or something bad happens when you try to install windows, all your documents will be safe on their own partition. 

i do this on my windows machines too. just redirect "My Documents" to it's own partition. it comes in handy when xp starts lagging. i can just reinstall windows without worrying about losing all my documents. (of course i back them up too, but...)

---

### Post by ed-koala on 2007-11-01
I can answer some of your questions.

I have the same type processor and memory as you do, so they work fine with Gutsy ... and Feisty.  I have a Nvidia graphics card, but an older GE Force card, tho just from reading these forums it seems Nvidia cards work ok.  I also have an IDE and SATA hard drive installed, and a CD Rom and DVD-RW drive.  All worked perfectly the first time.

I don't know about the motherboard but probably no problems there either, as it's what equipment the motherboard controls that is usually a problem.

Do check your printer, if any, for compatibility tho.  If you have a wireless network, check that too as it seems to be one of the things that might give you the most trouble.  Again, I just notice that from reading these forums, not from experience.

Last, I duel boot XP also, but each is on a different drive, so that made life easier.  Just look up duel booting here and you shouldn't have any problem at all.

---

