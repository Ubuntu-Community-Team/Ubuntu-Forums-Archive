---
title: "Ubuntu on old computers? LOW resources..."
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by gwilson on 2007-01-02
I'm setting up an afternoon tutoring center in an inner city area. Our equipment is REALLY old and limited, at the moment. I expect to get better hand-me-down computers soon, but for the time being, I need to run some form of Linux on this:

AMD K6 233 MHz
About 159 k RAM
4.2 MB PATA drive
Old 2 MB S3 video card
NEC Multisync XV14

I use Ubuntu on my home system and would like to stick with Ubuntu on these machines, if I can. I recently installed Xubuntu 6.1 from the alternate install CD successfully on a 3.2 GB drive, but it is painfully slow. I've tried Puppy, Feather and DSL. Feather actually seems to run best on the system described above.

So, what's the best way to install Ubuntu on a severely limited system? Can I do some sort of server installation that connects me with the Net and the do some sort of apt-get to load a lightweight desktop manager? Mostly, I need to have a word processor like Abiword and a browser like Firefox or Seamonkey. Storage space is not as critical as the demands of the program on resources. If it runs too slow, it's simply useless. The performance with Feather Linux is more or less acceptable.

I'm a Gnome guy, but I'm very flexible regarding desktop manager.

Thanks very much for your input.

Glen

---

### Post by bodhi.zazen on 2007-01-02
Fluxbuntu !

	[Main page](http://fluxbuntu.org/)

	[forums](http://community.fluxbuntu.org/)

	[ Download fluxbuntu-nbuild1-rev2-desktop-i386.iso](http://modzer0.cs.uaf.edu/~hardwarehank/fluxbuntu/rev2/fluxbuntu-nbuild1-rev2-desktop-i386.iso)

	MD5SUM  : 
	> c054428c46a1b5ffaab4295bc7db3c9b  fluxbuntu-nbuild1-rev2-desktop-i386.iso

Fluxbuntu review:  [http://techbycolin.com/?p=83](http://techbycolin.com/?p=83)

---

### Post by bobpur on 2007-01-02
I have an old IBM laptop that I was given about two weeks ago. It has similar specs to what you mention. 
If this helps you, I tried several Ubuntu distros and settled on Xubuntu v6.06.It runs really well and isn't molasses-in-January slow. I, also, tried Damn Small Linux (DSL) which my laptop liked. It required more tinkering to setup and I came back to Xubuntu. 
I'm new to linux too and Xubuntu was easy to install (Although slow). 
You might want to check out EasyUbuntu or [www.getautomatix.com](www.getautomatix.com) to help you with you with final prepping after the install.
As I understand it, you can install Gnome stuff later on Xubuntu. Xubuntu uses the xfce desktop manager (Hence the "X" in front of Ubuntu.

                                                                          Good Luck!

---

### Post by Lord Illidan on 2007-01-02
159k? You mean 159 Mb?

---

### Post by fiestaforever on 2007-01-02
> About 159 k RAM 

would fit nicely with: 

> 4.2 MB PATA drive

So he probably needs this: 

[http://freedos.sourceforge.net/](http://freedos.sourceforge.net/)  

:)

---

### Post by K.Mandla on 2007-01-02
Fluxbuntu or DSL, definitely. If you want some nifty low-level eye candy, you could try FVWM-Crystal on a server install of Ubuntu. :D

[center][[IMG]http://img144.imageshack.us/img144/7900/screenshot200701021050yx6.th.jpg[/IMG]](http://img144.imageshack.us/my.php?image=screenshot200701021050yx6.jpg)[/center]

(Granted, that's a P3-750 with an 8Mb ATI Rage Mobility, but you get the idea. :mrgreen:)

---

### Post by lyceum on 2007-01-02
I would have to second Fluxbuntu. nUbuntu runs great on a PC with 64 mb RAM, so I would guess that Fluxbuntu would work well on yours. (nUbuntu is a live CD with Fluxbox, like Fluxbuntu.) It takes a bit of getting use to, but it's pretty cool. If you can, I would try to up the stats though for better performance.

---

### Post by Lord Illidan on 2007-01-02
> **fiestaforever said:**
> > About 159 k RAM 

would fit nicely with: 

> 4.2 MB PATA drive

So he probably needs this: 

[http://freedos.sourceforge.net/](http://freedos.sourceforge.net/)  

:)

God, there's no way Xubuntu would have fit on that. Not even DSL.

---

### Post by Talon2 on 2007-01-02
Here is a list you might find handy:

[http://mypage.uniserve.ca/~thelinuxguy/small_and_floppy_linux/all.html](http://mypage.uniserve.ca/~thelinuxguy/small_and_floppy_linux/all.html)

---

### Post by k1001001 on 2007-01-02
> **Lord Illidan said:**
> God, there's no way Xubuntu would have fit on that. Not even DSL.
I think they meant 159 MB RAM and 4.2 GB HD. I have similar Packard Bell box with a 266 mhz processor, 40 MB RAM, and a 4 GB hard drive. I wonder how Ubuntu would run on that...

---

### Post by kerry_s on 2007-01-02
I would go for a custom build up with either "debian net install" or "ubuntu alternate cd". Start by installing a base system & then installing only what you need to get the job done. I have to do a build for a friend this weekend with a little better spec's than yours & i'm swinging towards "debian net install" cause it seems faster. I did a test install on my system last night so i can get familiar with it.

---

### Post by bodhi.zazen on 2007-01-02
> **k1001001 said:**
> I think they meant 159 MB RAM and 4.2 GB HD. I have similar Packard Bell box with a 266 mhz processor, 40 MB RAM, and a 4 GB hard drive. I wonder how Ubuntu would run on that...

Fluxbuntu has been reported to run on as little as 32 Mb RAM (although it takes 64 Mb to boot the live cd ; My understanding is the install was performed with 192 Mb RAM and RAM was then removed down to 32 Mb). Fluxbuntu HD install is just about 1.2 Gb.

Of course it is slow.

---

### Post by lyceum on 2007-01-02
> **kerry_s said:**
> I would go for a custom build up with either "debian net install" or "ubuntu alternate cd". Start by installing a base system & then installing only what you need to get the job done. I have to do a build for a friend this weekend with a little better spec's than yours & i'm swinging towards "debian net install" cause it seems faster. I did a test install on my system last night so i can get familiar with it.

That would work great for getting it installed, but I don't think it would make it run any faster.

---

### Post by Threbus5 on 2007-01-02
Hi,

Good for you.

My wife & I are in almost the same boat - tutoring service and computer wise.

We installed Ubunbtu 6.06 desktop and the educational software to a server (one of our newer machines that actually runs about 1.9 or so Ghz). Then we networked the older machines to the host using Xwindows. Although one old laptop with a 5.2 G HD seems to run Ubuntu 6.06 fairly well on its own it also does ok on the server <mostly>. <Mostly> because some progs such as Tux type seem very slow.

Take care.

---

### Post by Neural on 2007-01-02
When I first started evaluating distros, one of the small footprints distros that I evaluated that seemed impressive was SLAX
Perhaps the popcorn version with its listed apps seems tailor made for you? [Check it out here]("http://www.slax.org/download.php")

---

### Post by K.Mandla on 2007-01-02
I'd second that. Slax is very pretty for the size and speed you get. 

The Slax KDE desktop is about the only one I can stand in the KDE genre, and the XFCE (Popcorn) version is very clean and very old-school -- a big departure from what Xubuntu has become in it's Gnomified look.

If you like Slax, [Wolvix]("http://www.wolvix.org") is likewise fun.

---

### Post by Atreus12 on 2007-01-02
If it helps anyone, I had a laptop with 6GB hard drive, 600MHz and 64MB ram. I ran Xubuntu with fluxbox, but was still disappointed with performance. Even sitting idle after bootup, it was using ALL of my ram. I installed Damn Small Linux, and used that for a little bit, but didn't like it as much as Xubuntu. So I ended up buying more ram and Xubuntu with fluxbox runs well.

---

### Post by MattNuzum on 2007-01-02
Installation is always the tricky part. I've installed debian and then upgraded via apt-get over the net. You could probably (but I don't know how) use apt to do the upgrade from the alternate install cd.

Once you get the thing installed, you may find that it runs just fine. If not, you can always Ctrl+Alt+F1 and /etc/init.d/gdm stop and then install a different window manager using apt.

The first thing I would do is download the alternate install cd and try to install from it. Allocate the entire hdd to ubuntu, give 2xRAM or more as swap (so maybe 500MB would be good).

If that doesn't work, try the debian or dsl install then upgrade using apt.

dsl is a debian based linux and feels very familiar for an Ubuntu user. I've run it on Pentium 90/100 MHz computers with 1GB drives and 24MB of RAM. It will definitely work and with the extra cpu/ram you have you can easily modify it to make it look/feel more like ubuntu.

---

### Post by gwilson on 2007-01-02
Yes, that's 163,840 kB or around 160 MB.

Boy, you people were fast with the repies on this one!  

Thanks.

Yes, Xubuntu took FOREVER to install, even using the alternate ISO.

I was downloading Fluxubuntu already when I read the suggestion for it. So far, it's not happy about installing. Most of these "run or install" ISO's seem to require more memory to install the program than it actually takes to run it once it is on the hard drive. 

Fluxubuntu seems to have loaded itself to run as a live CD, but just as it gets to the payoff, my monitor goes blank. This old NEC has an LED in the front that's green when it has proper synch and turns orange when that goes away. It's orange now which probably means that Fluxubuntu has configured xserver with a default monitor that doesn't work with mine.

That's where I am at, right now.  Also, downloading Slax popcorn.

---

### Post by fiestaforever on 2007-01-02
Oh, I see, this is a serious thread. ;)  

With 159 MB of RAM, I would first check if some RAM is defective (how would you get to 159?).  
(EDIT: Oops, posted that before I could read your 160 MB statement.)

Then I would probably try an old favourite: Vector. 
[http://www.vectorlinux.com/]("http://www.vectorlinux.com/"). 

Or Zenwalk: [http://www.zenwalk.org/]("http://www.zenwalk.org/").

---

### Post by damianubuntu on 2007-01-02
I run three machines all  on about 233-450 celerons.  They all run fine on Xubuntu with 1 & 2 Gb drives (one is a master and slave of 1 gig each, root and home)b They have between 64 and96 mb ram and they run fine for normal desktop work.  Opera performed better than firefox BTW and of course dillo was a breeze.  BUT I did have to take a decent 256 mb from another machine and use it for the installs, and then give them back their original RAM.

Cheers

---

### Post by happy-and-lost on 2007-01-02
A while back I got DSL working extremely quickly (15 seconds to boot) on a 100Mhz P1 with 32MB RAM and a 1GB HDD. 'tis very good. A great thing about DSL is that it's (Or was when I used it!) fully Debian compatible, so adding better features is a breeze.

---

### Post by lyceum on 2007-01-02
> **gwilson said:**
> Yes, that's 163,840 kB or around 160 MB.

Boy, you people were fast with the repies on this one!  

Thanks.

Yes, Xubuntu took FOREVER to install, even using the alternate ISO.

I was downloading Fluxubuntu already when I read the suggestion for it. So far, it's not happy about installing. Most of these "run or install" ISO's seem to require more memory to install the program than it actually takes to run it once it is on the hard drive. 

Fluxubuntu seems to have loaded itself to run as a live CD, but just as it gets to the payoff, my monitor goes blank. This old NEC has an LED in the front that's green when it has proper synch and turns orange when that goes away. It's orange now which probably means that Fluxubuntu has configured xserver with a default monitor that doesn't work with mine.

That's where I am at, right now.  Also, downloading Slax popcorn.

As long as you are downloading stuff, check out DSL-N too (Damn Small Linux Not is not Damn Small Linux). It is bigger than DSL, but has more, and only need 64 MB of ram.

[http://www.damnsmalllinux.org/dsl-n/](http://www.damnsmalllinux.org/dsl-n/)

---

### Post by HeavyAl on 2007-01-03
I had a throw-away laptop from some guy I know a while back that had similar specs. In this case I just figured it was a foregone conclusion that Ubuntu proper wouldn't run on it so I stuck a copy of Slackware with BlackBox on it instead. Ran like a top. 

I prefer Ubuntu but I started out on Linux with Slackware .. if you're not afraid of the CL its not that difficult to get working.

I also recommend CRUX if you really want to customize your low end machines. Very stripped down. Very fast. And secure by default (ew, the BSD guys are gonna kill me!)

my 2c.

---

### Post by gwilson on 2007-01-03
Thank you for all of this good advice.

On this particular machine, Xubuntu is just too slow, but it would probably work fine with a box with just a little more oomph. Zenwalk 4.0 installed (long process) and might have run but didn't recognize the NEC monitor through the lousy video card, so I had a blank screen. On some distros, I was able to go into xorg.conf and correct the scan rates to fix this.

On to the smaller stuff!  I've tried DSL, Fluxbuntu, Slax-Popcorn, Feather and Puppy. At this point Fluxbuntu is the clear winner for me, but only due to my particular needs and wants. It looks good, runs reasonably well, and is fairly comfortable for an Ubuntu Gnome guy to use. It will be worth learning some of the fine points in terms of configuration because it looks like this distro has a future.

All of the other lightweight distros were very well designed for their intended uses, and each had particular strengths to recommend them. My personal preference is to stay more or less in the Ubuntu fold, if I can, so I think I will concentrate on Fluxbuntu for the present.

Thanks for all your input.

Glen

---

