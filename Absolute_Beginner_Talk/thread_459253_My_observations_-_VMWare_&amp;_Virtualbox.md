---
title: "My observations - VMWare &amp; Virtualbox"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by lazyart on 2007-05-30
My system- P4 2.0, 1.5 gb, 80 gb hd of which 60 gb is /home.

I have been using VirtualBox to use the two programs have have no Linux alternative.  I wanted to do the seamless access thing with rdesktop but somehome I borked it and spent a day getting the network working again.  It's just not as simple as it could/should be imho.

Yesterday I installed VMWare Server, gave it the same static 6 gig HD space in /home and 384 megs of RAM that I allocated for VirtualBox, installed XP and my software.  It's a piece of cake to do the seamless setup-- I selected a bridged network and I was off to the races.

I wasn't very impressed with the performance of VMWare.  The screen redraws were a tad slow and the mouse was not smooth at all.  I installed the Host Tools as it said it would help but I didn't see an appreciable difference.

Perhaps I did something wrong.  I was impressed that it can emulate multiple processors and even 64 bit processing.  In that it stands alone.  Performance wise (and I didn't choose either of those options) I preferred Virtual Box.

Naturally, your mileage may vary.

---

### Post by Bachstelze on 2007-05-30
Did you install VMWare Tools in your XP guest ? It increases performance a great deal.

---

### Post by lazyart on 2007-05-30
I did (i even remember it telling me the VM had to be running when I installed them) but I didn't see any difference. :(

---

### Post by starcraft.man on 2007-05-30
> **lazyart said:**
> 
I wasn't very impressed with the performance of VMWare.  The screen redraws were a tad slow and the mouse was not smooth at all.  I installed the Host Tools as it said it would help but I didn't see an appreciable difference.


Uh, speaking as a long time VMware workstation user (who has installed VMware tools hundreds of times), you must have done something wrong because I've never failed to get full speed performance out of a VM on VMware after installing the tools.

I also have an old p4 with 1 GB ram. So pretty sure it just has to do with how ya set it up.

Other than that, this should probably be in cafe or other place... beginner is more for actual problems.

---

### Post by Bachstelze on 2007-05-30
Running VMWare Server here and no problem at all either. Things run about 90% as fast as with a real XP.

---

### Post by lazyart on 2007-05-30
I'm totally wrong here and I apologize.  Apparently I hadn't installed the tools.

Performance is where it should be.

---

