---
title: "It just won't install"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by Tristicus on 2008-01-10
I have tried to install Ubuntu on this machine and it just will NOT GO! It is a celeron p4 with 1.5gb RAm, 40gb hdd, samsung dvd/cd-rw drive, and an QDI  board, PCI wireless card (maybe switch to USB), and an ATI Radeon 9000

IT WON'T INSTALL!

I have XP installed and that worked but Ubuntu won't.

WTF?

I have tried switching the cables, burning discs at the ABSOLUTE LOWEST SPEED POSSIBLE, and everything else. Alternate CD too!

---

### Post by Blutack on 2008-01-10
At what point is it going wrong exactly?

---

### Post by Tristicus on 2008-01-10
Well, when I remove the quiet splash on regular CD, it stops at CUPSD (Common Unix Printing System).

When I am installing using the alternate CD, it says it cannot install because the kernel will not install and even when I pick different ones it won't. 
The CDs are working as I used them for other PCs.

---

### Post by Hospadar on 2008-01-10
you might need a bios update.  My dad was having some trouble installing recently and a bios update fixed his problem.  Check your mobo manufacturer's website and see if they have any.  Make sure you follow their instructions exactly!  it's easy to botch a bios update if you don't do it like they say to do it and kill a bios, which then has to be sent in to get reprogrammed.

---

### Post by Tristicus on 2008-01-10
Thanks!

---

### Post by gruss on 2008-01-10
I also had problems installing 7.10 on one pc, so I tried 6.06 cause i had that cd laying around too and the install went just fine.  Still havent figured out why the new version of ubuntu wouldnt go...but 6.06 is fine for what that pc does.  Might be worth a shot if you dont need the latest and greatest

---

### Post by K.Mandla on 2008-01-10
> **Tristicus said:**
> I have tried to install Ubuntu on this machine and it just will NOT GO! It is a celeron p4 with 1.5gb RAm, 40gb hdd, samsung dvd/cd-rw drive, and an QDI  board, PCI wireless card (maybe switch to USB), and an ATI Radeon 9000

IT WON'T INSTALL!

I have XP installed and that worked but Ubuntu won't.

WTF?

I have tried switching the cables, burning discs at the ABSOLUTE LOWEST SPEED POSSIBLE, and everything else. Alternate CD too!
Keep in mind that other distributions might prove better at setting up your hardware, so if you can bear to step away from Ubuntu, you might try something different that's also Linux. 

In any case, it would be something of a troubleshooting measure, since you'll have an idea if your hardware arrangement is the problem, or if it's something within Ubuntu that's giving you problems.

---

### Post by Tristicus on 2008-01-10
[http://www.qdigrp.com/qdisite/eng/support/d_biosp4.htm](http://www.qdigrp.com/qdisite/eng/support/d_biosp4.htm)

My board is a Superb 4FX board with SIS 648FX+SIS 963 chipsets.
There is no BIOS update there.

---

### Post by Tristicus on 2008-01-10
[http://www.pcconsult.cz/detail.php?item=416&odkaz=34&id=5](http://www.pcconsult.cz/detail.php?item=416&odkaz=34&id=5)
This is the board right here.

---

### Post by Blutack on 2008-01-10
Could you edit the options of the live cd to include

> noacpi

and then try booting please?

(This will help you add the option [https://answers.launchpad.net/ubuntu/+question/6837](https://answers.launchpad.net/ubuntu/+question/6837))

---

### Post by Tristicus on 2008-01-10
All I do is just remove EVERYTHING and put that?

---

### Post by Tristicus on 2008-01-10
Tried both of the options, NOACPI and NOAPIC, and neither worked. I have no freaking idea what is wrong with this heap. STOPPED at the SAME place. 4 bars and 1/8th of a fifth left.

 XP runs on it fine (I am in it right now) but Ubuntu won't run at all.

---

### Post by Tristicus on 2008-01-10
Anyone???

---

### Post by Tristicus on 2008-01-10
Can ANYONE OFFER HELP PLEASE!?

---

### Post by eolson on 2008-01-10
At this point,  I think I'd try burning another cd.  There's always the possibility that that one got damaged somehow since the last time you used it.

---

### Post by Tristicus on 2008-01-10
I have tried 3 or 4 cds all burned at lowest speeds and checked for integrity.

---

