---
title: "What's the purpose of having 2 Start Ubuntu on LiveCD?"
date: 2007-08-24
forum: Beginner Team
---

### Post by jingo811 on 2007-08-24
What's the purpose of having 2 Start Ubuntu options at Boot when using the LiveCD?
Today at school there was around 40 guys trying to install Feisty.  The level of experience ranged from Super newbies to old über veterans.  Still both of those divided personalities fell into the trap of choosing the first option rather than the 2:nd safe graphics mode.

And I would say 90% of all fell into the trap and then made their first installation have an incorrect resolution.
Since most ppl in that classroom was veterans they simply modified the XORG.conf file.  But seeing this phenomenon happen you could say that Linux first timers doing the install at home all alone will face a BIG obstacle.

Since they don't know how the terminal works. 
They don't dare messing with system files since it's their first Linux experience.

[IMG]http://i14.tinypic.com/52pphth.png[/IMG]



Long story short :) What's the purpose of having 2 Start Ubuntu options at Boot when using the LiveCD?  
When most of the times the first option always screws up the screen.  Wouldn't it be better if the LiveCDs in the future only offered the safe graphics mode.  Then there wouldn't be as much resolutions failures for newcomers.

---

### Post by scrooge_74 on 2007-08-24
My take on this from personal experience.  On some laptops it would go with no problem on the first option.  On others things got too slow to try to install the system.. Then tried the safe mode option and installation was as speediest as I have come to know.

---

### Post by aysiu on 2007-08-24
I don't think the idea is that *most of the time the first option always screws up the screen*.

I'd say most of the time the first option works just fine. You use the second option *when* the first option screws up the screen. It's a second resort.

---

### Post by bernied on 2007-08-24
Is this just a scenario of a room full of identical computers, all with the same graphics adapter that the installer doesn't deal with very well?

I've never had any trouble with the first option (on 4 different machines).

---

### Post by dulbirakan on 2007-08-24
Many machines not one problem...

---

### Post by bapoumba on 2007-08-25
Used it once, when I had grub messed up on install. My DD was not properly declared. Boot on the DD from the LiveCD and fixed it ^^

---

### Post by jingo811 on 2007-08-25
> Is this just a scenario of a room full of identical computers, all with the same graphics adapter that the installer doesn't deal with very well?

I've never had any trouble with the first option (on 4 different machines).

40 identical hardwares. :smile:  with some integrated Intel graphics chipset.  But before this I've tested it on my 2 PCs at home one bought from around ~2004 and another ~2006.  Not the latest hardwares but still enough specs to handle the latest Win XP - 3D games on the market.  And the other is just hardwares picked for Linux and surfing needs.

Still they both ( ATI and Nvidia ) didn't handle the first install option well using LiveCD at boot.  I mean how many Linux newcomers would know that if you install with the 2nd option then things will be as smooth as with a Windows installation.  
My observation from the experience  tells me that even Linux veterans fell into this trap!  There should be some kind of graphics test just like there is a CD check test on LiveCD.
( **You should make a poll on this question for newbies to have some sort of finger pointing statistics to go by! **)
Besides how many Linux newcomer would care to waste another 30 minutes on installation procedures when they already spent 30 minutes on the first bad resolutions install. ( **poll this also** )


Also you should poll about how many ppl managed to install propers screen resolutions with the **first Install option** or if they had to use **Safe graphics mode**!  
This can be fixed by changing one simple line in xorg.conf file naturally, but from the newcomers point of view messing with xorg.conf the first thing they do with Linux is very unlikely especially when they all sit alone at home.  Maybe with some outdated Linux for Dummies book from 1994 for Redhat beside them :)
....Then they come to the Ubuntuforums crying with a 100 questions EACH all at once.



Long story short.  My point is that I think the future LiveCDs should do things the other way around.
Install with the xorg.conf **"vesa"** options **by default ** or something....and instead let old Linux veterans do the neccessary work if they wanna squeeze every drip on their graphics card.  

As of now the Windows newcomers have to take the TECHNICAL hit first by facing xorg.conf hardware issues alone.  Before they even have setup their mp3s, work files, and having fun with customizing the graphical stuff on GNOME feeling around the Ubuntu system.
By doing things the other way around it would be much better if the Linux veterans took the TECHNICAL hit first, then newbies just follow like zombies when they ask.....me thinks!

---

### Post by jingo811 on 2007-08-25
Shorthanded response of the above long post :) :

There should be a comprehensive Graphic card check just like there's a check for the CD.  Before doing the final Installation process in future LiveCDs.
So that one doesn't have to guess whether the **First Install option** will be good enough or if you need to use **Safe graphics mode**.  From lone newbies point of view using Linux for the first time.

---

