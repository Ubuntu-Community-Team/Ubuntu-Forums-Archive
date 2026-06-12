---
title: "AMD64 or i386?"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by shaft350x on 2007-02-28
I've been running on Edgy Eft 6.10 the 64bit version.  Since I have an AMD64 processor. (My setup is in my signature).  I've been running this for a few months now, but because most programs are still for 32 bit versions I have more trouble getting things to work.  I just got my system to where my wife's laptop can print to the printer connected to my Ubuntu computer.

I really want to get compiz/beryl working, and wine (so I can get a few programs for school to work in Ubuntu).  I'd also prefer to get Flash working as well.  I have tried to get all of these working, and I have been unsuccessful in getting them to work.

I am in the middle of a semester and already playing catch up because of family issues, so something intensive right now is out of the question, but what should I do?  Is it possible to force the i386 version of Ubuntu on the AMD64 architecture?  Would that make it easier for me to get all of these things working since 64bit doesn't seem to be the priority?  Should I try to force the 32-bit stuff to work in the 64bit version of Ubuntu?  Or should I just try and suck it up and wait for more 64-bit compatibility?

I know that there are a ton of questions here, and I'm not even sure if I'm using the right terms or if those suggestions are possible.  Just wondering what direction I should be looking at taking.  Thanks in advance for any advice.

---

### Post by x64Jimbo on 2007-02-28
I recommend switching to 32 bit, but unfortunately, that will be "intensive." Give yourself a couple hours to get it done, but most of your problems will be fixed. The 64 bit processors are completely compatible with i386 Ubuntu.

---

### Post by jvc26 on 2007-02-28
I reinstalled after a while with 64bit and have decided to wait a bit for more 64 compatibility - that arriving is only a matter of time now. I run the 32bit on my 64bit (AMD64 3200+) processor with no problems (was that a question or did I wrongly infer that?) You can force architectures, but it can be messy and probably isnt worth the extra trouble. You don't gain all that much performance wise with the 64bit at the moment, unless you're doing very intensive graphic/video editing. Consequently there isnt that much reason to keep with the 64 so if its not too much trouble you could change back to 32bit - it doesnt take that long.
Il

---

### Post by shaft350x on 2007-02-28
Thanks for the help.  I think I initially tried to install the i386 version, but had problems (it has been a while and I think it may have actually been with Windows and needing a scandisk run before everything was cleaned up properly, which happened with the 64 version)

The next thing I suppose is should I stick with Edgy Eft, get Feisty, or go down to Dapper?  (The last one I want to avoid because things didn't seem to work quite the way I wanted them too and now I'm fairly used to Edgy)

Will installing the i386 version overwrite my 64bit version?

---

### Post by janz84 on 2007-03-01
> **shaft350x said:**
> Thanks for the help.  I think I initially tried to install the i386 version, but had problems (it has been a while and I think it may have actually been with Windows and needing a scandisk run before everything was cleaned up properly, which happened with the 64 version)

The next thing I suppose is should I stick with Edgy Eft, get Feisty, or go down to Dapper?  (The last one I want to avoid because things didn't seem to work quite the way I wanted them too and now I'm fairly used to Edgy)

Will installing the i386 version overwrite my 64bit version?


Stick with Edgy until Feisty is released on April 19th.

---

### Post by in_flu_ence on 2007-03-01
I think if you need a smooth system right from the start for general work. 32bit will be fine and the choice since you won't see too much more performance for using a 64bit OS.

I, for one, use 64bit OS. Yes it does give me some problem at times but I take the fact that it will also be the chance to get closer to know about the OS. Might even be able to find some tips for the community. So it depends on if you want a stable and working system or trying with the latest. Note: I also need the 64bit compability for my scientiific softwares though.

I think I would choose Edgy rather than dapper even though there is the LTS. Edgy is very stable in my opinion if you do not try to break it yourself. It has alot of repos and packages that will keep you going.

I would say no to Feisty as yet till it has been officially released.

---

### Post by shaft350x on 2007-03-02
Well with trying to play catch up at school it may be until after Feisty is released that I can really concentrate on trying to reload Ubuntu.  I've got it setup so I can print and my wife can print from her laptop, so that will be good for now.  Thanks again for all of your help!

---

### Post by x64Jimbo on 2007-03-02
No problem. Thanks for asking first rather than just taking the plunge blind. You saved yourself a lot of hassle and made our jobs easier.

---

### Post by shaft350x on 2007-04-26
Ok so Feisty is out and I have already downloaded a copy of the i386 version.  Since I am running the x64 version of Edgy I don't think I can just upgrade from the CD right?

So what will be the easiest way to get Feisty on my desktop?

Also I read somewhere about someone adding a separate partition for their home folder so they would not loose their files on an overwrite of the operating system.  Just wondering if you all would suggest this, and if you know of a how to which would make this easy for me?

(Still probably be a few weeks before I actually make the move from EE to FF because we're in the final weeks of classes.)  Thanks again for all your help!

---

### Post by igknighted on 2007-04-26
> **shaft350x said:**
> Ok so Feisty is out and I have already downloaded a copy of the i386 version.  Since I am running the x64 version of Edgy I don't think I can just upgrade from the CD right?

So what will be the easiest way to get Feisty on my desktop?

Also I read somewhere about someone adding a separate partition for their home folder so they would not loose their files on an overwrite of the operating system.  Just wondering if you all would suggest this, and if you know of a how to which would make this easy for me?

(Still probably be a few weeks before I actually make the move from EE to FF because we're in the final weeks of classes.)  Thanks again for all your help!

Save whatever files you need to removable media (cd/thumbdrive/floppy?!?!) and do a fresh install.  You could separate off a partition and move everything in /home there, then mount it as /home (DO NOT FORMAT IT DURING INSTALL) in your new install.  If you do this make sure to use the same username/password.

---

### Post by shaft350x on 2007-05-04
well just did the switch.

Got the printer shared through CUPS (since now all computers have Ubuntu, no more Windows as a first option anyways)

Now I can't get my mouse buttons to work, which they did before in Edgy.  Went through the same process and no dice.  I'll keep working on it.

So it will probably be a little while before I get things back to the way I liked them, but priorities are a little different this time around.  I want to see if I can actually get things loaded with WINE and get flash, and then get everything all customized (ie Beryl, desktop effects work for me, but I like the fine tuning available for Beryl)

Thanks for the help all!

(I didn't do the /home folder thing when partitioning.  Is it still possible to do after the install?)

---

