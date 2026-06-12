---
title: "So...Compiz and ATI drivers?"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by mrapoc on 2007-12-20
Ive been told after creating a thread on my...poor performance when enabling any effects that basically compiz + ati = no good. Is this strictly true and when are we expecting a fix? Even when turning on "normal" effects with both standard restricted drivers (within ubuntu) or the latest - scrolling on internet pages becomes jittery/laggy, and performance generally sucks. 

I am going to be getting a 8800gt soon for the main rig, so are the nvidia drivers better? Or should i say, fully functional? 

Shame my laptop which im about to migrate over to ubuntu...has ATI graphics..:(

---

### Post by rockin_goliath on 2007-12-20
Every system with Nvidia graphics that I've tried has rocked with compiz. After a bit of tweeking with Advanced Compiz Settings Manager, there is not a tear to be seen when moving windows around!

---

### Post by mrapoc on 2007-12-20
so the ati issue is universal? not just me...being a n00b :D

that sucks majorly - so all ati users have to make do with no effects?

---

### Post by tdeboeser on 2007-12-20
Well no.  I've run Beryl/compiz on good Nvidia AND good ATI's. I've even run beryl on a built-in generic Intel graphic card. 

Nvidia had better linux support that ATI ( ATI doesn't seem to care much about the linux community ).  And all my Ubuntu desktops do better with [Envy's ]("http://albertomilone.com/nvidia_scripts1.html") help.  Give it try.  

That said Compiz is like Vista, you need a decent card to get to do well.


Tom de

---

### Post by mrapoc on 2007-12-20
Is there anything you recommend over compiz for general "niceness". Sure the ubuntu default interface is ok, once you theme it but even so, XP classic still looks better (maybe im exaggerating). 

What do you recommend for my main rig? 8800gt, core 2 duo @ 3.0ghz, 2gb of ram 

And my laptop - Turion X2 @ 1.6ghz, 2gb of ram and ATI 1250xpress graphics

I know how to theme etc. but i presumed compiz was the only effects worth getting

cheers

---

### Post by ugm6hr on 2007-12-20
> **mrapoc said:**
> so the ati issue is universal? not just me...being a n00b :D

that sucks majorly - so all ati users have to make do with no effects?

Nope. I have an ATI Radeon Xpress 1100 graphics card in my laptop - and Compiz works great.

Maybe this thread might help:
[http://ubuntuforums.org/showthread.php?t=580748](http://ubuntuforums.org/showthread.php?t=580748)

---

### Post by mrapoc on 2007-12-20
I thought XGL was a major resource hog?

Ill try that anyway on my fresh laptop install :)

---

### Post by Phoenixzeus on 2007-12-21
Last time I checked ATI did not have opensorce drivers, so I can't see this problem getting too much better until (and indeed if) they release opensorce drivers.

---

### Post by ugm6hr on 2007-12-21
> **mrapoc said:**
> I thought XGL was a major resource hog?


No idea.  But it works.  And I haven't noticed any slow-down on 2GHz AMD Turion, 2GHz RAM.

I don't really like lots of effects - so I only use the animations, opacify, expo and ring switcher (which I think are all useful).  I do have desktop wall on, but I rarely use multiple desktops now.

---

### Post by GeorgiaBoot on 2007-12-21
I think it is more ATI than anything. I have an ATI card and my system is good but Compiz just does not like it. 

If you have to have those Effects get a new card or wait for ATI Drivers (If they ever come out!)

My only problem is when I move open windows it becomes very garbled, but that's life :)

---

### Post by tdeboeser on 2007-12-21
(Repost):  If you have a decent vid card pls try [Envy]("http://albertomilone.com/nvidia_scripts1.html") ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html))

It will get you the best driver and recompile your kernel for you.  I found regular video performance to greatly improved.  

Also, a word on opensource vid drivers;  Even with Nvidia the OEM drivers perform better.  I have a box with an GeForce 7600 GS w/512MB.  With the 'nv' driver I find regular xwindowing to fine.  But loading the the OEM driver not only improved performance but allowed me to reliably run compiz, and run more compiz features.

The difference between ATI and Nvidia isn't the availability of opensource drivers, but the company's dedication to writing good drivers for linux. 

Tom de

---

