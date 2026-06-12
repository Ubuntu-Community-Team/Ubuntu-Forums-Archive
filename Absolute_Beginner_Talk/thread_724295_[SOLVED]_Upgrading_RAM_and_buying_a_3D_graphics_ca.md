---
title: "[SOLVED] Upgrading RAM and buying a 3D graphics card"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by Berean on 2008-03-14
Hi, I'm wanting to upgrade my 3 year old laptop (specifications; Fujitsu-Siemens Amilo D7850, Intel Pent.4 from 2.66GHz Celeron, 512mb/80gb, ATI Radeon 9200 graphics, 1024x768) as when running VMware with Windoze XP (more specifically, Libronix digital library) my virtual machine is very slow.  I've performed free -m and got the following read-out:

ian@ian-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           503        497          6          0          1        219
-/+ buffers/cache:        276        226
Swap:         1474         33       1440

My questions are;

1. With the above readout and the virtual machine running slowly would it be prudent to upgrade my RAM to say 1gb, or even higher?
2. Would that speed everything up, or is it simply because I have a virtual machine running that's the problem and not speed itself?
3. Would upgrading RAM give me any noticeable increase in speed throughout Ubuntu 7.10 (it's NOT slow at present).
4. I have some limited effects with Compiz using the above graphics card.  If I installed a (cheap) 3D graphics card would that have any bearing on the issue of speed, or simply improve graphics?  I am not a gamer, but would like some more desktop graphics.
5. Will either increased RAM or a 3D graphics card be expensive?
6. Can I get any hardware to fit my machine?

I'm relatively new to Ubuntu, so please treat me as though I know nothing!  Thanks in advance for your advice.  Regards

---

### Post by drdrewdown on 2008-03-14
good luck putting a video card in the laptop... your radeon should suffice..

more memory would def help you running a vm

i wouldn't run anything less then 2gb if your board supports it

that would increase your performance 10fold

---

### Post by Berean on 2008-03-14
drdrewdown,

Thanks for your post.  How will I know if my motherboard will support it?  Also, would you advise against getting a 3D graphics card?

---

### Post by Therion on 2008-03-14
Overall that's not a bad little laptop.  I'd say it's worth putting a little money into if you plan on using it for a while longer...

> **Berean said:**
> 
My questions are;

1. With the above readout and the virtual machine running slowly would it be prudent to upgrade my RAM to say 1gb, or even higher?
Yes.  I would say so, even if not a great deal.  1GB, I think, would be about the sweet-spot.  2GB MIGHT be a little overkill, but you can never have "too much" memory in my opinion.

> **Berean said:**
> 2. Would that speed everything up, or is it simply because I have a virtual machine running that's the problem and not speed itself?
I'd say you have a combination of things slowing you down, memory being one of them.  Celerons are not my favorite processor, but it's certainly adequate for Ubuntu.  It's got some raw speed (at 2.6Ghz) even if throughput is less than what it could be.  

> **Berean said:**
> 3. Would upgrading RAM give me any noticeable increase in speed throughout Ubuntu 7.10 (it's NOT slow at present).Nothing is certain, but I would think it would.

> **Berean said:**
> 4. I have some limited effects with Compiz using the above graphics card.  If I installed a (cheap) 3D graphics card would that have any bearing on the issue of speed, or simply improve graphics?  I am not a gamer, but would like some more desktop graphics.
Hard to say.  This is one of those "it depends" questions.  As in "it depends" on how cheap a card you install and what that card is.  What's cheap to you... $20, $50, $100?  A more capable graphics solution will take some of the strain off of your CPU, but you've already got a dedicated graphics card, so it's hard to say what the result would be without knowing exactly what it is you want to do.  

> **Berean said:**
> 5. Will either increased RAM or a 3D graphics card be expensive?
See above... What's expensive to you?  RAM is one of the cheapest upgrades you can perform relatively speaking.

> **Berean said:**
> 6. Can I get any hardware to fit my machine?
Most likely you can, but like what exactly?  Most laptops have very limited upgradability.  Some, but nothing like a desktop.

---

### Post by drdrewdown on 2008-03-14
you should go to the manufacturers website & check specs for the model number of your laptop.. it should give you specs on maximum memory supported by bank & total.

also, since you have a laptop, you probably aren't going to upgrade the video card. you are stuck wit that imo

be sure you know which type of memory your board supports.. its most likely DDR

be sure you know there is a difference in memory types if you go to upgrade..

---

### Post by Berean on 2008-03-14
Thanks to both of you!  Good advice, and I'll definitely look on the Fujitsu website.  Here's looking to a faster Ubuntu experience.  Kind regards,  Ian.

---

### Post by Berean on 2008-03-14
Therion,

[QUOTE=Therion;4515131]Overall that's not a bad little laptop.  I'd say it's worth putting a little money into if you plan on using it for a while longer...

I DO plan on using this a little longer.  What would you suggest?

---

### Post by Therion on 2008-03-14
> **Berean said:**
> Therion,

[QUOTE=Therion;4515131]Overall that's not a bad little laptop.  I'd say it's worth putting a little money into if you plan on using it for a while longer...

I DO plan on using this a little longer.  What would you suggest?[/QUOTE]
Memory upgrade first.  1GB total system memory minimum, 2GB if it's within your budget.  I have no idea what memory you'll need, though most likely it's pretty standard DDR as was mentioned previously. Nor do I know much it will cost, so this is a cost/benefit thing only you can decide on.  Check with the manufacturer for specs on your RAM just to be sure.  I'd be stunned if it couldn't handle 2GB though.

Next would be an upgrade to the video, if that's possible.  I'm no expert when it comes to mobile video solutions, so I can't give you specific suggestions, but 1. find out if it's even *possible* to upgrade your video card and then, 2. do some research on what your options are.  Again, it's a cost benefit analysis only you can do and I can't make promises about how much improvement you'll see, if any,  by doing these upgrades.  All you can say for certain is that it won't HURT anything!  Take your time though, and do your research.

---

