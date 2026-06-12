---
title: "[SOLVED] Should I upgrade my RAM?"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by farueulogy on 2007-12-11
I run mint linux based on ubuntu 7.04 and was wondering if it was worth upgrading my RAM.

It is currently 768MB and everything runs pretty smoothly except for the occasional hang in firefox. I was thinking of going up to 2GB.

Will make much of a difference or be worth it?

When I tried 7.10 before it was unstable - could this be fixed by an increase in RAM?

---

### Post by jordanmthomas on 2007-12-11
RAM is the best upgrade for the money and if you're running out often, more will improve your experience.
That said, I do fine with only 512 MB.

---

### Post by PartisanEntity on 2007-12-11
I have 2GB of RAM and I too find that Firefox will hang from time to time. So I don't think it has anything to do with your amount of RAM. Depending on which desktop environment you use, you can have a smooth running system even on weaker or older hardware. Try XFCE or IceWM.

---

### Post by kpkeerthi on 2007-12-11
Well.. that depends on how intense your computer is put to use. Check if your system is swapping by running
```

free

```
when you feel your system is crawling. Frequent swapping is probably an indication that you need more RAM.

You already have sufficient RAM. So I don't think your firefox crash is attributed to it.

---

### Post by farueulogy on 2007-12-11
> **kpkeerthi said:**
> Well.. that depends on how intense your computer is put to use. Check if your system is swapping by running
```

free

```
when you feel your system is crawling. Frequent swapping is probably an indication that you need more RAM.

You already have sufficient RAM. So I don't think your firefox crash is attributed to it.
```

             total       used       free     shared    buffers     cached
Mem:        775600     737108      38492          0      19308     371204
-/+ buffers/cache:     346596     429004
Swap:      2273156          **0**    2273156

```
I take that as none of my swap is being used?

I guess I should ask about my firefox/7.10 woes more specifically - Thanks guys.

---

### Post by ajkirchner on 2007-12-11
Running a Thinkpad T43 with a Pentium M @ ~1.8 and same graphics card (ATI radeon x300)

just upgraded my RAM from 512 to 1GB and I can notice a slight difference - probably shoulda just went all the way up to 2GB since RAM is pretty cheap nowadays - bought a 512 chip from Newegg for about 15$

i say why not - upgrading RAM is the cheapest performance boost you can get

---

### Post by rockinlinux on 2007-12-11
Having more RAM never hurts. I am running 2GB and have never had anyhting hang with Ubuntu. RAM is getting to be pretty cheap now days, if you think more RAM will help or you plan on doing lots of Video, graphics or sound work then you should get more RAM. On other thing to look at is how many (if any) slots you have open.

honestly though you have plenty of RAM for ubuntu unless you are doing major video editing and stuff.

---

### Post by OrangeCrate on 2007-12-11
Before anyone decides whether you need more RAM or not, take a look at this...

**Linux Memory Management or 'Why is there no free RAM?' **

> Traditional Unix tools like 'top' often report a surprisingly small amount of free memory after a system has been running for a while. For instance, after about 3 hours of uptime, the machine I'm writing this on reports under 60 MB of free memory, even though I have 512 MB of RAM on the system. Where does it all go?

[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf)

Similar thread on RAM here:

[http://ubuntuforums.org/showthread.php?t=624148](http://ubuntuforums.org/showthread.php?t=624148)

---

### Post by Pumalite on 2007-12-11
Memory is to be USED and Linux does it very well.

---

### Post by Partyboi2 on 2007-12-11
>  When I tried 7.10 before it was unstable - could this be fixed by an increase in RAM?I am running the same amount of ram you are (768 ) I didn't really have any problems with Gusty.

---

### Post by laidback on 2007-12-11
I would ask myself..How long will this computer last? If you reckon you'll get value from the new RAM over that period of time, or the ram can be moved into a newer pc, then go for it. Otherwise stick with what you have until such time as you upgrade the system.

---

### Post by jaybombalous on 2007-12-11
I have a different outlook on this issue...

My theory is this... if u ever think u **might** want to have memory available for something without the thought of having to **swap out** data, then your answer is to buy more memory.

---

### Post by jaybombalous on 2007-12-11
> **laidback said:**
> I would ask myself..How long will this computer last? If you reckon you'll get value from the new RAM over that period of time, or the ram can be moved into a newer pc, then go for it. Otherwise stick with what you have until such time as you upgrade the system.


with the market right now??? LOL, buying anything as a deal now a days almost means your computer is outdated before u even get to use it.

---

### Post by philinux on 2007-12-11
Firefox 3 looks very promising. I just tried out alpha 8 from the repo and it renders sky news, and this website much faster. They've also been plugging most of the memory leaks too.

---

### Post by SunnyRabbiera on 2007-12-11
well firefox 2 hangs anyhow so really there is nothing wrong with your setup, heck even I do pretty fairly at my modest specs... though I am gonna get my puter upped eventually

---

### Post by farueulogy on 2008-03-28
I've decided not to upgrade my RAM. I've been running 7.,10 fine since I've installed the restricted drivers.

---

