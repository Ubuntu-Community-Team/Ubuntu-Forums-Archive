---
title: "Ubuntu 6.10 and my desktop?"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by OhioYJ on 2007-02-05
After using Ubuntu 6.10 (32-bit version) on my laptop for several weeks, I'm ready to make the switch on my desktop. However, I can't get the live CD or any option from the CD to work on my desktop.

My Hardware:

AMD64 3800+ Dual Core
Asus A8N-SLI Deluxe
2 - BFG 7800GTs in SLI
1 - SATA Raptor HD
2 gig of ram.

I'm using the same CD I used on my laptop, and it checks out ok, but for some reason it always locks up as soon as the screen turns tan, and it starts opening up the GUI. 

I'm guessing if the live CD doesn't work, its probably not going to work on my hardware?

---

### Post by taurus on 2007-02-05
Perhaps the LiveCD is having a little technical difficulty with your graphic card.  In the meantime, try using the alternate CD instead.

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

---

### Post by OhioYJ on 2007-02-05
> In the meantime, try using the alternate CD instead.

Thanks for the input, downloading it as we speak. I'll let you know what happens.

---

### Post by OhioYJ on 2007-02-05
Nope no luck, the alt CD does the same thing, locks up in the same place as the live CD. 

So you think its the video cards, or the SLI thats messing it up?

---

### Post by Maestro23 on 2007-02-05
> **OhioYJ said:**
> Nope no luck, the alt CD does the same thing, locks up in the same place as the live CD. 

So you think its the video cards, or the SLI thats messing it up?

Try disabling the SLI. Just run one card and see what happens.

---

### Post by irish_flu on 2007-02-05
I have a system almost identical to yours, except that my Video card is a 7600GS (just one, no SLI) and I'm using only IDE hard drives.  Same motherboard.  For some reason I have problems booting to just about ANY cd.  I'm truly not sure why.

Sometimes, several tries, I get get it to boot to a Windows XP cd or to an Ubuntu cd.  I've never successfully booted to a 64-bit Ubuntu CD.  Of course, mine fails to recognize the disk at all (yeah, my BIOS is set up right) so my problem is probably different....

Anyway, good luck to you.  I'm with previous poster that you should temporarily run without SLI and see what happens.

---

### Post by OhioYJ on 2007-02-05
> I'm with previous poster that you should temporarily run without SLI and see what happens.

Yeah but that is only a tempoary solution, it would verify whether or not the SLI is the problem, but I don't want to give up my SLI just to run an OS. Is Ubuntu capable of running SLI?

---

### Post by irish_flu on 2007-02-05
> **OhioYJ said:**
> Yeah but that is only a tempoary solution, it would verify whether or not the SLI is the problem, but I don't want to give up my SLI just to run an OS. Is Ubuntu capable of running SLI?
Well, assuming that the problem does turn out to be SLI, once you install Ubuntu you can load drivers from nvidia.  At that point, as far as I know, you'll be able to use your SLI.

I'm *guessing* that if SLI turns out to be the problem, then it's because there can onyl be so many driver configurations loaded onto the one-size-fits-all live CD.

---

