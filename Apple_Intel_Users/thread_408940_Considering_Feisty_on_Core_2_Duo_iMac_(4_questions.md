---
title: "Considering Feisty on Core 2 Duo iMac (4 questions)"
date: 2007-04-14
forum: Apple Intel Users
---

### Post by Slackpacker on 2007-04-14
(not urgent at all, take your time)
I would dual-boot my 24" 2.16 GHz C2D iMac.  I'm still wondering...

-should I wait for Feisty Final?

-what's the worst case scenario if I screw up?  Is hardware damage a possibility at any point?  Can I recover from my OSX boot disc?  Horror stories please!

-should I use the AMD64 version?  How can I check that both CPUs are utilized?

-based on the [MacBook howto]("https://help.ubuntu.com/community/MacBook"), what (if anything) do I need to enter at the boot prompt?  What is this "lpj" command anyway?

Any other advice or links are most welcome!

---

### Post by roadkilla on 2007-04-14
I would definitely recommend waiting for the final version of Feisty Fawn this is a bumpy road for all
of us that have installed Feisty Fawn in the beta stages every once in a while comes an update
that render the system unusable so I think you should wait for the final version if you are a newbie at Linux.

you can use AMD64 version or the regular 32Bit version SMP Kernel will be used automatically
but for the best performance you should install AMD64 as this version works best with C2D processors
 but it comes with it's own share of problems I suggest you do a little preemptive reading
before jumping into the pool with the AMD64 version.

you MUST specify lpj parameters in order to boot successfully a Mac computer in Ubuntu
**lpj=8645184** - this is for Core 2 Duo 2.16Ghz
why this is needed I have no idea... I know this is related to the CPU timer

worst case scenario, you'll have to wipe your hard drive clean and start over.
no you can't destroy your hardware this way :D ..

---

### Post by cyberdork33 on 2007-04-14
> **roadkilla said:**
> you MUST specify lpj parameters in order to boot successfully a Mac computer in Ubuntu
**lpj=8645184** - this is for Core 2 Duo 2.16Ghz
why this is needed I have no idea... I know this is related to the CPU timer

That's not true, I have a Core2 Duo 20" iMac @ 2.16GHz, never specified the lpj and have never had a problem

---

### Post by Chrisj303 on 2007-04-14
> **cyberdork33 said:**
> That's not true, I have a Core2 Duo 20" iMac @ 2.16GHz, never specified the lpj and have never had a problem


Same here - not a singled failed boot / kernel panic, not once.


606

---

### Post by Gen2ly on 2007-04-14
The AMD64 install, installs a 64bit system.  I must note that 64bit systems aren't nearly as well supported as 32bit.  Applications not rigged to 64bit can be run in 32bit emulated mode but will take a perfomance hit.  Aren't some things like Flash not available in 64bit mode?  I run x86 version and like it's stability and lack of bugs.

---

### Post by H264 on 2007-04-16
Well, I had to reformat and install OSX again, but that was due to me being confused about order of operations. I could do it again with no problems. But I installed it (64 bit version) when it was still in alpha stage, now I would bet it is nicer and easier to install. As far as incompatibility goes, I'm not having any issues with anything yet.

[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607) This thread looks like a good collection of threads on the topic, check em out and come back here with questions

[http://ubuntuforums.org/showthread.php?t=388143](http://ubuntuforums.org/showthread.php?t=388143) is for limited flash support, personally I don't care for flash and could do without. But it looks like it will work alright if you follow the instructions

[http://ubuntuforums.org/showthread.php?t=384230](http://ubuntuforums.org/showthread.php?t=384230) is my thread on dual booting OSX and 7.04 64bit.

---

### Post by roadkilla on 2007-04-17
yes I know there are workarounds to 64bit....
and I made a mistake lpj is needed to be specified to macbook I think other apple machine
can live without it...:D

---

### Post by ronocdh on 2007-04-17
> **Dirk.R.Gently said:**
> The AMD64 install, installs a 64bit system.  I must note that 64bit systems aren't nearly as well supported as 32bit.  Applications not rigged to 64bit can be run in 32bit emulated mode but will take a perfomance hit.  Aren't some things like Flash not available in 64bit mode?  I run x86 version and like it's stability and lack of bugs.

Dirk I know you mean well, but I must protest the FUD against 64-bit Ubuntu. I welcome the OP to check out the 64-bit forums, where you'll find solutions for just about anything. Kilz in particular is an extremely helpful guy, and his sig has scripts for getting Flash working (I mention that because it was the only hard example you gave).

Also, I too recommend you wait for Feisty Final. I always prefer to install a new version freshly from a CD, rather than upgrade through the console, and it would be silly to recommend you do that twice within a week! Also, the changes in the GUI installer should be pretty slick. Enjoy, and--in a way--I hope to be seeing you posting back here soon! ;)

---

### Post by Slackpacker on 2007-04-17
Thanks for all your advice!  I was somehow under the impression that 64-bit was required for this system.  I'll probably use it anyway, since I'm fairly confident I can get Flash, etc. working (and it isn't critical if I can't).  I'd also seen something about heat problems in AMD64, but that is probably FUD.  I wonder if this lpj thing will be fixed in Ffinal...  

Seems like the worst thing I could do would be to accidentally wipe out my OSX partition or misconfigure the Linux partition and have to wipe that and start over.  Could problems in the Linux partitions affect the OSX partition too?

---

### Post by buschi on 2007-04-17
> **roadkilla said:**
> ... lpj is needed to be specified to macbook ...

that's what you can read in many places -- i never specified it though and experienced no kernel panic on my macbook c2d (feisty herd 5). so i guess it's not needed any more...

---

### Post by roadkilla on 2007-04-19
it is best to set it, although you might not get kernel panic or see any symptoms I gather that the CPU timer  is
misbehaving on apple computers with Linux and the **lpj**  variable set the timer exactly to what it should be.
I think that on the Macbook it is mandatory if I'm not mistaken. so yes it works without it but I think it will works better with it.

---

### Post by irow82 on 2007-04-20
I am trying to install 7.04 AMD64 final on my MacBook Pro (C2D 2.16) using parallels, but I am getting an error when I try to boot off the the live cd. Ubuntu says: "Your CPU does not support long mode. Please use a 32 bit distribution."

The C2D is 64 bit, I have the Vt-X box checked. Any idea what am I doing wrong?

Thanks

---

### Post by balt on 2007-04-20
I don't think Parallels supports 64bit. Try the 32bit version.

Cheers

- Balt

---

### Post by Chrisj303 on 2007-04-20
> **irow82 said:**
> I am trying to install 7.04 AMD64 final on my MacBook Pro (C2D 2.16) using parallels, but I am getting an error when I try to boot off the the live cd. Ubuntu says: "Your CPU does not support long mode. Please use a 32 bit distribution."

The C2D is 64 bit, I have the Vt-X box checked. Any idea what am I doing wrong?

Thanks

I installed the 64-bit ubuntu on my macbook using the latest VMware Fusion (Beta 3) - no problems whatsoever.
For Mac users wanting to run Linux via VM, Fusion is the way to go - parallels seem to have given up on us!
When Fusion goes gold, it will be an absolute must-have.

303

---

