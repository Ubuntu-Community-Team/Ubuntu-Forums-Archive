---
title: "Photoshop Woes!!"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by Stickymaddness on 2007-04-03
:cry: I'm disparately seeking a way to get Photoshop to run on Ubuntu! I am aware of the open source alternatives to Photoshop, so please don't point me there!!

I'm running 6.10 and have gone through all the the guides I can find and still haven't had any luck. I've tried CS2 and at best it starts up but crashes after using it for a few seconds. Photoshop 6.0 starts loading up and then crashes and disappears. 

I've tried both using Wine to install, and copying over from a NTFS drive that has it installed. Neither of them have yielded any success :cry:

Any help would be _greatly_ appreciated!!

---

### Post by taurus on 2007-04-03
Have you tried CrossOver Office?

[http://www.codeweavers.com](http://www.codeweavers.com)
[http://www.codeweavers.com/products/cxoffice/](http://www.codeweavers.com/products/cxoffice/)

---

### Post by Terl on 2007-04-03
A check at Codeweaver's site (crossover linux and Wine) show it is known not to work with wine, as you noticed.

Crossover shows it as not working.

---

### Post by hyper_ch on 2007-04-03
Depending on your computer you could run photoshop within a virtual windows running on vmware or virtualbox....

---

### Post by jvc26 on 2007-04-03
I'd +1 for the use of a VM it gets you (depending on your pc's speed) a much better method of launching windows native apps which you cant get to work properly in wine.
Il

---

### Post by Stickymaddness on 2007-04-03
> **taurus said:**
> Have you tried CrossOver Office?

[http://www.codeweavers.com](http://www.codeweavers.com)
[http://www.codeweavers.com/products/cxoffice/](http://www.codeweavers.com/products/cxoffice/)

Awesome!! Got Photoshop 6 working, and it seems to be pretty stable! Tried to see if I could crash it, and it runs fine thus far, shortcuts 'n everything! 

Web optimize runs a little slower than in windows, but it's a minor sacrifice to make!!

Thanks!! You rock!! :grin:

---

### Post by kc5hwb on 2007-04-03
Did you use VMware?  Or something else?  I am about to try to do this myself and I was planning on using VMware.

---

### Post by Stickymaddness on 2007-04-04
> **kc5hwb said:**
> Did you use VMware?  Or something else?  I am about to try to do this myself and I was planning on using VMware.

No, I used Cross Over Office [http://www.codeweavers.com/products/cxoffice/]("http://www.codeweavers.com/products/cxoffice/")

Good luck!

---

### Post by thefoolisme on 2007-04-04
I can't wait to try this.  I'm a photoshop person, and Gimp, as good as it is, is just not the same. I can't get the codeweavers website to open right now.  Does it say it will work with newer Photoshop versions too?

---

### Post by alextj on 2007-04-04
Just as a reminder - Cross Over Office is not free and it probably cannot run the latest PS without problems.
But wmware server is free and you can damn sure run anything that runs on Windows, if you have a Windows installation CD and a decent computer.

---

### Post by wieman01 on 2007-04-04
Just to confirm that CrossOver Office works with MS Office XP. It is stable as a rock and integrates well with KDE. I am impressed. 40 USD wisely spent.

---

### Post by Stickymaddness on 2007-04-04
> **thefoolisme said:**
> I can't wait to try this.  I'm a photoshop person, and Gimp, as good as it is, is just not the same. I can't get the codeweavers website to open right now.  Does it say it will work with newer Photoshop versions too?

Agree with you there, gimp just isn't the same! I was sooo happy when I got Photoshop up and running!! Unfortunately though, the highest version that is supported is Photoshop 7. You could still attempt it with a higher version though...

---

### Post by david_kt on 2007-04-04
> **alextj said:**
> Just as a reminder - Cross Over Office is not free and it probably cannot run the latest PS without problems.
But wmware server is free and you can damn sure run anything that runs on Windows, if you have a Windows installation CD and a decent computer.

VMware is free, BUT, you need to buy license of the windows OS you installing on vmware. So, in this case, vnware is much more expensive than crossover office, and much more slower as it isrunning on emulation mode.

DK

---

### Post by Stickymaddness on 2007-04-04
> **david_kt said:**
> VMware is free, BUT, you need to buy license of the windows OS you installing on vmware. So, in this case, vnware is much more expensive than crossover office, and much more slower as it isrunning on emulation mode.

DK

Surely it would be ALLOT slower, since you are emulating an entire OS and then Photoshop on top of that? I reckon your ram would take a bit of a beating from that.....

---

### Post by alextj on 2007-04-04
Based on my personal experience, it's not any slower. Though, I do have a fairly fast PC.

---

### Post by P_Badger on 2007-04-04
Photoshop 7 definitely works in Crossover Linux.

---

### Post by david_kt on 2007-04-04
> **alextj said:**
> Based on my personal experience, it's not any slower. Though, I do have a fairly fast PC.

That is depend on how much memory your system has. If your system has 1 giga memory, then you could use 500 MB for emulation. It is still pretty fast, but still cut your memory by half. If you have 500 mb, then you spilt it into two, 250 for host, 250 for emutalion, still not so bad although you will start seeing the slow down. But if your system just only has 250 mb, then your system would be crawling.

Wine on the other hand, do not need to split memory at all.

DK

---

### Post by Stickymaddness on 2007-04-06
> **alextj said:**
> Based on my personal experience, it's not any slower. Though, I do have a fairly fast PC.

Yes, but what I meant to say was, that while it isn't any slower, it's more efficient to emulate an application rather than an operating system and the application. For example, I'd rather burn 128mb of ram than 256mb, regardless of the fact that you don't notice a difference in performance...

---

### Post by alextj on 2007-04-08
> **Stickymaddness said:**
> Yes, but what I meant to say was, that while it isn't any slower, it's more efficient to emulate an application rather than an operating system and the application. For example, I'd rather burn 128mb of ram than 256mb, regardless of the fact that you don't notice a difference in performance...

But, if you have the resources, why not use them?
I have 1280MB DDR and I don't really care how much of it wmvare uses (hell, let it take all of it! =P), as long as things work good and fast for me. Though, if you really have something like 256, then you should definitely go for WINE (or xoffice), I guess... Then the only option is PS7 (or older?). Of course it's nicer to have only the app running, you can skip loading Windows, but your CS2 isn't going to work.

---

### Post by userundefine on 2007-04-08
Wine is not an emulator.  Anyway, CS2 working on Linux with anything is anecdotal at best.  My advice would be to analyze exactly what features CS2 offers that previous versions that work well with wine don't, and weigh the costs.  Or, like others suggest, run it via VM which is what I'd recommend as well.

---

### Post by Shay Stephens on 2007-04-08
You can get Photoshop 7 working with wine, see my signature, but non of the CS version currently work.

---

### Post by Stickymaddness on 2007-04-12
> **Shay Stephens said:**
> You can get Photoshop 7 working with wine, see my signature, but non of the CS version currently work.

I'm currently running Photoshop 6 with crossover office, and it runs perfectly so far. Only thing that doesn't work is web optimizing a .gif file, how does this handle with wine?

---

### Post by Shay Stephens on 2007-04-12
> **Stickymaddness said:**
> I'm currently running Photoshop 6 with crossover office, and it runs perfectly so far. Only thing that doesn't work is web optimizing a .gif file, how does this handle with wine?

If you follow the how-to in my signature, you can run "save for web" successfully.

---

### Post by Stickymaddness on 2007-04-12
> Using the linux path in the past has killed the ability to "Save for web" in Photoshop. So stick with the windows path for now.

There was my problem... I still can't run Photoshop stably using wine how ever, but I should be able to do this in crossover office.

---

### Post by Shay Stephens on 2007-04-12
> **Stickymaddness said:**
> There was my problem... I still can't run Photoshop stably using wine how ever, but I should be able to do this in crossover office.

What version of wine?  I am running .9.34 with much success.  But try the xorg.conf step to see if that helps with the crossover version.

---

### Post by Stickymaddness on 2007-04-12
> **Shay Stephens said:**
> What version of wine?  I am running .9.34 with much success.  But try the xorg.conf step to see if that helps with the crossover version.

I was using .9.30 and I didn't do the xorg.conf step. However I have it working beautifully under crossover, so I ain't gonna fix what ain't broke..... ;) 

I'm saving that for CS2...coz it's horribly broke :/

---

