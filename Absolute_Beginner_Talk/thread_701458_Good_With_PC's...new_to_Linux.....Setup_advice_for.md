---
title: "Good With PC's...new to Linux.....Setup advice for System needed!!!"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by Guitaraholic on 2008-02-19
Hi everyone,

Ive never used Linux in my lfe but through the advice of some friends have told me about Ubuntu and Im very interested in setting it up. 

I recently built myself a new Rig and i have seen afew potential problems i could have....just enquiring to any solutions to these problems to make my setup of ubuntu as stress free as possible.

Spec:

Quad core E6600 OC'd@ 3Ghz
Evga 680i Mobo
4gig OCZ Nvidia EPP Ram PC-6400
XFX 7600GT XXX edition GFX
3x Western DIg Raptor 16MBcache  250Gig HDD's

Apparently I could have a number of Issues with this setup.....
This is what ive found so far....

1. Ubuntu does NOT detect the LAN ports on this Mobo.....
2. Drivers for GFX card..do they work? I plan on installing compwiz-fusion or Beryl.
3. Does it utilize the Quad core n 4gig ram?

Also are they any other issues I could have with this hardware setup????

I do know quite a bit about PC's in general just sick of XP n vista in general......

Thanks for the help

---

### Post by Mongoose.wa on 2008-02-19
The graphics card should work. I have an 8600M GT laptop card and the drivers are fine.

---

### Post by Guitaraholic on 2008-02-19
oh right thats good to hear!

I had to play with some settings at first you see bcos my card being an OC'd one doesnt have default res n was causin all saorts of gfx issue when bootin off the disc. Just use the standard drivers off nvidia with that then?

any info about the problem with the LAN ports n solving that???

thanks in advance!

---

### Post by Paqman on 2008-02-19
> **Guitaraholic said:**
> 
1. Ubuntu does NOT detect the LAN ports on this Mobo.....

If that's the case, i'd be inclined to use a different mobo. Not having an internet connection during install/setup can make solving any problems difficult. If you know you're going to have at least one problem to solve, you're already in difficulty. Unless you've got a solution that you know is going to work (and be easy) then this mobo is probably more trouble than it's worth.
> 
2. Drivers for GFX card..do they work? I plan on installing compwiz-fusion or Beryl.

Yes, the Nvidia drivers are good. Compiz is installed by default on most recent distros. With Ubuntu you'll be up and running in a few mouse clicks.
> 
3. Does it utilize the Quad core n 4gig ram?

Of course. You'll want to use the 64-bit version to get the most out of your RAM.

---

### Post by Paqman on 2008-02-19
> **Guitaraholic said:**
> Just use the standard drivers off nvidia with that then?


If the default drivers are no good then the best thing to use might be [Envy](http://albertomilone.com/nvidia_scripts1.html). It'll install the latest drivers automatically.

---

### Post by Guitaraholic on 2008-02-19
cheer for that info!

Ive read the problem is due to the chipset not giving the kernal files the correct info.....im thinking of just installing ubuntu n trying to fix the LAN problem n check the internet on my laptop......

ive seem afew things on the internet to solve it but i dont reali understand some of it!

just a solution to fix this for when i install it will be good!!!!!

---

### Post by bernied on 2008-02-19
> **Guitaraholic said:**
> 1. Ubuntu does NOT detect the LAN ports on this Mobo.....
If your location is Liverpool, uk, you can get a new LAN PCI card for under a fiver from [ebuyer](http://www.ebuyer.com/product/132470). In fact I might have one at home I could sell you one for that much. You could have it on Thursday.
Cheaper than a new mobo.

---

### Post by Guitaraholic on 2008-02-19
good idea actually haha!

if the problems isnt resolved soon prob will go with that idea.......
ive prob got a NIC sitting round in one of my old pc's tbh

n will that be auto detected in ubuntu?

cheers!

---

### Post by Paqman on 2008-02-19
> **Guitaraholic said:**
> cheer for that info!

Ive read the problem is due to the chipset not giving the kernal files the correct info.....im thinking of just installing ubuntu n trying to fix the LAN problem n check the internet on my laptop......


That'll work. There are people on these forums who will be able to diagnose and fix your problem. Have a crack at some of the solutions you've found online, but don't hesitate to ask here for help.

---

### Post by Guitaraholic on 2008-02-19
yea thatnks for the help so far!

im gona set my ubuntu up from ive got a free day off so i can get it working straight off .....lookin at afew diff things like comwiz-fusion.....beryl......wine.....etc

also idea of dual display with extended desktop etc.....

ill sort them out once ive got ubuntu up and working first i think!

definately looking forward to using ubuntu once its working!

---

### Post by stchman on 2008-02-19
> **Guitaraholic said:**
> Hi everyone,

Ive never used Linux in my lfe but through the advice of some friends have told me about Ubuntu and Im very interested in setting it up. 

I recently built myself a new Rig and i have seen afew potential problems i could have....just enquiring to any solutions to these problems to make my setup of ubuntu as stress free as possible.

Spec:

Quad core E6600 OC'd@ 3Ghz
Evga 680i Mobo
4gig OCZ Nvidia EPP Ram PC-6400
XFX 7600GT XXX edition GFX
3x Western DIg Raptor 16MBcache  250Gig HDD's

Apparently I could have a number of Issues with this setup.....
This is what ive found so far....

1. Ubuntu does NOT detect the LAN ports on this Mobo.....
2. Drivers for GFX card..do they work? I plan on installing compwiz-fusion or Beryl.
3. Does it utilize the Quad core n 4gig ram?

Also are they any other issues I could have with this hardware setup????

I do know quite a bit about PC's in general just sick of XP n vista in general......

Thanks for the help

Everything should work just fine.

I have a 7600GT vid card and it works.

My advice is to load up the LiveCD and give a test drive.  Unless you have some really funky hardware it should be fine.

The 32 bit version will use that memory.  4GB of RAM is the max any 32bit OS can address.  You can use Ubuntu 64bit if you like.

Yes, the 4 core CPU will be utilized.

---

### Post by Fred_E _krugar on 2008-02-19
That board should have two nic ports make sure you are using etho 0 Ubuntu should have no problem. I have the same board in my other comp with two 7900GTO's.

---

### Post by Guitaraholic on 2008-02-19
oh good to know the prots will work!!!

had a couple of ppl tellin me they dont always work.....i will try it when i set it up


thanks for the info guys!

---

