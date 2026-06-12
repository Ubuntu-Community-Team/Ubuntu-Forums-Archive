---
title: "Why am I having trouble running a linux distro on my old laptop?"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by Bwangster12 on 2007-11-13
This is the laptop I have: [http://juljas.net/linux/vaiofx240/](http://juljas.net/linux/vaiofx240/)

I have tried to install a number of different distros on my old laptop. 

Xubuntu installs but is extremely lethargic.  I am used to windows... but it appears that its slow like when you don't have enough memory or something.

The system specs for Xubuntu appear to be 128 to install and 64mb to use.  I have 128mb of ram in this old laptop and it is a Pentium 3 with about 14gb of harddrive.  I don't think the CDRW/DVD drive is fantastic.  I have had issues when trying to run LiveCDs off of it because I guess its slow.

Shouldn't Xubuntu run very nice with 128mb of ram?  Could the graphics drivers need updating?  Could the harddrive be partitioned badly?

---

### Post by taurus on 2007-11-13
Try Fluxbuntu.

[http://www.fluxbuntu.org](http://www.fluxbuntu.org)

---

### Post by Bwangster12 on 2007-11-13
I did give that a shot... but I was getting weird activity.  The coloring and graphics looked messed up and it seemed buggy.  Whether that related to my computer or the fact that the distro is very new, I don't know.

---

### Post by jimrz on 2007-11-13
> **Bwangster12 said:**
> I did give that a shot... but I was getting weird activity.  The coloring and graphics looked messed up and it seemed buggy.  Whether that related to my computer or the fact that the distro is very new, I don't know.

128 really does not run the "live" cd and is not enough to install from it. I would suggest downloading and installing from the Xubuntu "alternate" cd, which it should handle just fine.

---

### Post by Bwangster12 on 2007-11-13
Thing is... the regular CD wouldn't even work, so I have been using the Alternate CD.  

Once I install Xubuntu off the Alternate CD... its lethargic.  What cud be the reason for this?  Isn't 128mb of ram enough?

---

### Post by wngraham on 2007-11-13
I have an old HP Laptop with almost the exact same specs, and installing Ubuntu from the live CD was painfully slow before eventually stopping altogether. I then tried the alternate install CD (as suggested above) and have been running 7.04 for months and now 7.10 with no problems at all.

---

### Post by taurus on 2007-11-13
> **Bwangster12 said:**
> Thing is... the regular CD wouldn't even work, so I have been using the Alternate CD.  

Once I install Xubuntu off the Alternate CD... its lethargic.  What cud be the reason for this?  Isn't 128mb of ram enough?

How did you set up your harddrive?  How much space did you give to swap partition?

---

### Post by jimrz on 2007-11-13
> **Bwangster12 said:**
> Thing is... the regular CD wouldn't even work, so I have been using the Alternate CD.  

Once I install Xubuntu off the Alternate CD... its lethargic.  What cud be the reason for this?  Isn't 128mb of ram enough?

Have heard that 128 is sluggish. You might try fluxbox or, if you can, add some ram - even just going to 256 should yield pretty good boost in performance.

---

### Post by Bwangster12 on 2007-11-13
Well... as of yesterday, I hadn't even dabbled with the partitioning.  

I tried running Gparted LiveCD and the GUI wouldn't boot up, so someone suggested Puppy Linux and then just use Gparted from the menu.

This is what I had...

hda1 7.69 GB BOOT PARTITION

hda5 1.54 GB

hda6 4.74 GB

I changed it to just an hda1 and an hda5 with basically the same sizes.  After that I didn't install anything else.  

I am very raw with regards to partitioning.

---

### Post by houstonbofh on 2007-11-13
This guy is the master of Linux on old systems. [http://kmandla.wordpress.com/](http://kmandla.wordpress.com/)  This is his guide for gutsy. [http://kmandla.wordpress.com/2007/10/20/howto-set-up-gutsy-for-speed/](http://kmandla.wordpress.com/2007/10/20/howto-set-up-gutsy-for-speed/)  Spend some time reading his site, and go from there.

---

### Post by hyper_ch on 2007-11-13
xubuntu live cd runs on 128mb ram ;)

also does xubuntu run on 128mb ram... but I think it will still be slow... a light-weight window manager probably would be better (as suggested with fluxbox).

---

### Post by linuxlizard on 2007-11-13
I've got an old laptop too- a p3 700 mhz with 192 mb ram. I purchased it a couple of years ago for hardly anything and then went through several weeks of pulling my hair out and learning that linux on old hardware isn't what all the fans say it is.

Xubuntu ran like a slug on it. I've never tried fluxbuntu. I've also run puppy linux, damn small linux, vector, etc, and pulled my hair out every time. Linux for the most part has become bloated.

BUT- I've found 2 that run really well on it and aren't "broken" versions like puppy or dsl, but normal, full linux. The first is zenwalk and it ran very well, but compared to ubuntu, the package selection is slim and it's a little wierd.

 PCFLUXBOXOS however runs like lightning on it, has synaptic and a full compliment of packages similar to ubuntu to choose from, if not quite as many still a great selection, has a modern kernel and up to date software and is just amazing. Boots up in less than 30 seconds to the log in and from login to desktop takes another 2 or 3. Stuff pops open and it feels as fast or in some ways faster than my ubuntu desktop which is an athlon 2800+ with 756 mb ram. So it's very impressive.

Ubuntu's still my favorite, but for old hardware- pcfluxbox probably can't be beat.

---

### Post by Whiffle on 2007-11-13
I might get flamed for saying this, but I'd suggest trying another distro.  Ubuntu on its own has quite a bit of bloat I've noticed, lots of stuff that loads even if you don't need it (kernel modules for example).  Changing the desktop environment doesn't make much of a differece, which is what your'e doing by going to xubuntu.

---

### Post by Bwangster12 on 2007-11-13
Hmm... PCFluxboxOS seems to be similar to TinyMe.  Both look to be derivatives of PCLinuxOS.

When I uses the LiveCD and ran TinyMe off of that, the desktop seemed quite smooth and fast... but when I went to use the installer my machine would "crap" out.  I presumed it had to do with my CDRW/DVD drive being slow I guess.  Someone in that forum mentioned it sounded like me running out of memory.

The installer froze at the partioning screen.  If I tried to use existing partitions it still froze.

---

### Post by Bwangster12 on 2007-11-13
> **Whiffle said:**
> I might get flamed for saying this, but I'd suggest trying another distro.  Ubuntu on its own has quite a bit of bloat I've noticed, lots of stuff that loads even if you don't need it (kernel modules for example).  Changing the desktop environment doesn't make much of a differece, which is what your'e doing by going to xubuntu.

Well thing is... I have changed the desktop environment.  I've tried Puppy Linux and DSL and just do not want to use either.  Both remind me of something like Windows 98.  They do not seem up to date.

Fluxbuntu is buggy on my machine.  I understand that because it is new.

When I installed Xubuntu but used Fluxbox or IceWM, it worked well... but not everything was compatible.  I am very much a Linux lamen... so I didn't know how to bring back all the options I needed.

---

### Post by Whiffle on 2007-11-13
[http://www.vectorlinux.com/](http://www.vectorlinux.com/)  maybe?

---

### Post by Bwangster12 on 2007-11-13
I definitely have no problem trying other distros...

But what exactly is the problem when trying to run things like Xubuntu?  I'm the type of person who is open to a change, but likes to know the reason, lol.

Shouldn't I be able to run Xubuntu a bit more smoothly?  The Xubuntu webpage says it takes 64mb to run.  Shouldn't my laptop not crap out when trying to install "TinyMe?"  I thought TinyMe and these mini distros were built for my laptop.

---

### Post by 900donuts on 2007-11-13
i have been working on turning a laptop older and more out of date than yours into a media player useing debian 4.0 etch see here [http://forums.debian.net/viewtopic.php?t=21004](http://forums.debian.net/viewtopic.php?t=21004) so as a result i recommend you try a minimal install of debian and tailor it to your needs

---

### Post by Bwangster12 on 2007-11-13
I think I'd rather buy another 128mb stick of ram to install so I can use Xubuntu rather than having to tinker with other distros that I am even MORE unfamiliar with.

Would having 256mb or RAM basically solve these issues I am having when trying to install Xubuntu, TinyMe, gOS?

---

### Post by oldos2er on 2007-11-13
> **Whiffle said:**
> [http://www.vectorlinux.com/](http://www.vectorlinux.com/)  maybe?

 I agree. Vector Linux standard with xfce would do the job nicely, IMO.

---

### Post by houstonbofh on 2007-11-13
Being the last post on the page you may have missed it.  Read this. [http://kmandla.wordpress.com](http://kmandla.wordpress.com)  He uses Ubuntu, Arch, and several others.  He will tell you how to remove lots of Ubuntu bloat. It is the best source of how to cram modern linux on small machines out there.  An example is [http://kmandla.wordpress.com/2007/09/03/meet-the-little-laptop-that-could/](http://kmandla.wordpress.com/2007/09/03/meet-the-little-laptop-that-could/) which is a K6-2 450 with 256 meg of ram, or [http://kmandla.wordpress.com/2006/09/20/getting-6061-on-120mhz-pentium-15gb-48mb](http://kmandla.wordpress.com/2006/09/20/getting-6061-on-120mhz-pentium-15gb-48mb) which is a 120Mhz Pentium 1.5Gb 48Mb!

---

