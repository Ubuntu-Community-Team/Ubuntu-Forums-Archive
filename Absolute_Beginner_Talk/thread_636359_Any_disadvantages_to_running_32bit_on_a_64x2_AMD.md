---
title: "Any disadvantages to running 32bit on a 64x2 AMD?"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-12-09
I just got a laptop. AMD 64x2. I just put the 32 bit version on it and was like... aww... maybe I should have gotten the 64 bit.

Is there much of a difference? All I can remember with the 64 bit version is a year or so ago it was awful compared to the 32 bit version. Nothing was stable on it yet. What's the update now?

---

### Post by jordanmthomas on 2007-12-09
Well, if you have 4GB of RAM or more, you can't access it in 32-bit.
I think the only real "problem" left in 64-bit is that Adobe hasn't released a 64-bit flashplayer yet so you still have to run the chrooted firefox.

There's other differences, like things running faster since they're optimized for 64-bit as well.

---

### Post by Wynne G Oldman on 2007-12-09
> **Roasted said:**
> I just got a laptop. AMD 64x2. I just put the 32 bit version on it and was like... aww... maybe I should have gotten the 64 bit.

Is there much of a difference? All I can remember with the 64 bit version is a year or so ago it was awful compared to the 32 bit version. Nothing was stable on it yet. What's the update now?

I'm running 64 bit Gutsy, and its fine. There's a few programs that there isn't 64 bit versions avilable yet, but all in all, I don't have any problems. Best thing to do is try it, see what you think, and if you don't like it, you can always go back to 32 bit. It's nice to be able to use your hardware to it's full potential though.

---

### Post by roaldz on 2007-12-09
> **Roasted said:**
> I just got a laptop. AMD 64x2. I just put the 32 bit version on it and was like... aww... maybe I should have gotten the 64 bit.

Is there much of a difference? All I can remember with the 64 bit version is a year or so ago it was awful compared to the 32 bit version. Nothing was stable on it yet. What's the update now?

I´ve only been using 64bit ubuntu on my core2duo lappie, and so far no real problems concerning 64bit software. It´s stable (at least I dont have serious hangs, I don´t know how much more I have them, compared to an equal 32bit install).
A while ago it was difficult to install flashplugin-nonfree in 64bit Firefox, but those problems are over too:)
I´d suggest (if you think you need to use 64bit) that you should install it, and check it out:)

Roald

---

### Post by jordanmthomas on 2007-12-09
> **roaldz said:**
> A while ago it was difficult to install flashplugin-nonfree in 64bit Firefox, but those problems are over too

Well, then disregard what I said.  :)

---

### Post by Wynne G Oldman on 2007-12-09
> **jordanmthomas said:**
> Well, if you have 4GB of RAM or more, you can't access it in 32-bit.
I think the only real "problem" left in 64-bit is that Adobe hasn't released a 64-bit flashplayer yet so you still have to run the chrooted firefox.

There's other differences, like things running faster since they're optimized for 64-bit as well.Just to elaborate, all you have to do when you need to use Flash in Gutsy, is when prompted to install it, just choose yes, and it installs it for you. You still can't use Flash in 64 bit versions of Windows yet, as far as I'm aware.

---

### Post by szymon_g on 2007-12-09
hm... there *is* a way to use more than 4gb of ram on 32platform...

---

### Post by roaldz on 2007-12-10
> **szymon_g said:**
> hm... there *is* a way to use more than 4gb of ram on 32platform...

Well, and what would that be..?

---

### Post by MrKlean on 2007-12-10
I just set up a dual boot with 64 and 32 on my laptop...if I'm not mistaken ( which does happen a lot LOL!)  I think there is a 64bit flash...I remember installing it..or at least a solution.. there wasn't when gutsy first came out..

---

### Post by jordanmthomas on 2007-12-10
> Well, and what would that be..?
It's easy...rebuild your kernel to have 64-bit support.  :)

---

### Post by roaldz on 2007-12-11
> **jordanmthomas said:**
> It's easy...rebuild your kernel to have 64-bit support.  :)

But are you still running a 32bit platform then?

---

### Post by Red Moose on 2007-12-11
Can you run 32-bit software on Ubuntu 64-bit?

---

### Post by Harpoon on 2007-12-11
Compatability is basically a libraries issue:  the developers chose not to provide the 32 bit libraries by default on the 64 bit OS (pre Gutsy, anyway).  This is easily taken care of using the repos to install the ia32libs packages.  As 32 bit stuff gets deb'd for the 64 bit platform, these are included in the dependencies, so it gets even easier.

The only glitches I have found are things like running flash enabled 32 bit Swiftweasel:  I need to close any 64 bit instances of firefox, etc. *before* opening swiftweasel32.  At worst, this is a minor inconvenience if I don't plan ahead.  I have installed, used, removed other 32 bit apps without problems.  For those that have raised issues, searching the forums either provides a solution or proves that the problem lies with the app, and not the architecture - - both 32 and 64 bit users are having the same problems.

On a 64 bit laptop, hardware seems to have fewer problems (for me) using the 64 bit OS (e.g., sound issues and such).

Summary:  There is no overwhelming reason why you must use 64 bit, and no overwhelming reason why you should use  32 bit. 

Feisty; core2duo 1.6 ghz; 2gb ram; intel sound, graphics, wireless.

---

### Post by Red Moose on 2007-12-11
That makes me feel better.  I was thinking about buying an Athlon64x2 computer, but I was worried that there wasn't going to be enough 64-bit software.

---

### Post by awthomp on 2007-12-11
I have a 64 bit and run Gusty 32 bit.  I haven't noticed any major performance issues - but then again, I have pretty good hardware and don't require too much of my machine.  I find 32 bit easier to use in many instances (I had troubles with flash in 64 bit).  

Plus, before I switched from Kubuntu to Ubuntu, I had MANY display problems with my Nvidia 8500GT graphics card on the 64 bit system.  These problems vanished with 32.

---

### Post by brad1138 on 2007-12-11
Well, it looks like there are few disadvantages in running 32-bit, what are the advantages of running 64-bit?

Brad

---

### Post by rsambuca on 2007-12-12
> **brad1138 said:**
> Well, it looks like there are few disadvantages in running 32-bit, what are the advantages of running 64-bit?

Brad

Anything that requires processing power:  video editing/transcoding, audio transcoding, 3D rendering, compiliations...

---

