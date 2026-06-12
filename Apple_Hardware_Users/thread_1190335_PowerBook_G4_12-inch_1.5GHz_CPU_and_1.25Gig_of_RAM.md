---
title: "PowerBook G4 12-inch 1.5GHz CPU and 1.25Gig of RAM."
date: 2009-06-17
forum: Apple Hardware Users
---

### Post by ayenack on 2009-06-17
Hello all.

I'm about to come into the possession of an PowerBook G4 12-inch 1.5GHz CPU and 1.25Gig of RAM.

I've been using GNU/Linux for years and Ubuntu for a couple of years full time on most of my comps. But a Mac is new to me and I want to run Ubutnu on it if at all possible.

Anyone got any ideas as to the best version for the above mac with support for most if not all of the hardware?

Thanks in advance for any help.

---

### Post by shizumasa14 on 2009-06-17
You can't.  The power book uses PowerPC technology which is not supported.

---

### Post by ayenack on 2009-06-17
I've had a look at this in the sticky.

[http://ubuntuforums.org/showthread.php?t=427714](http://ubuntuforums.org/showthread.php?t=427714)

So it can be done just not sure how well it'll support my hardware.

---

### Post by jangari on 2009-06-17
I'm intending to give this a go myself; about to acquire the same powerbook. The link to the PPC live CD images (for Jaunty) is [here]("http://cdimage.ubuntu.com/ports/releases/jaunty/release/"). 

Just give the live CD a go and see how it works before you install it. I've read that bluetooth can be a bit of a pain and the trackpad doesn't work too well, but I read that of Dapper Drake, so thinkgs may be much better now.

Let me know how it works.

---

### Post by MikeTheC on 2009-06-17
shizumasa14: You're not actually serious, are you?

@OP and @jangari:

Clearly you can read for yourselves the Mac-oriented sections of this message board. Indeed, I would highly encourage you to do so.

Now, that being said, the two questions I have to ask you are:

1. What do you intend to use a Linux PPC Mac for?
2. What specific features are critical to you, and which ones are you willing to give up?

Bear in mind a few things...

First, PPC is dated technology. This means that many of the optimizations and tweaks for x86, especially in recent years, don't necessarily have equivalents in PPC. It doesn't mean that PPC can't run Linux at all, or even that it can't run it well. As a matter of fact, I have a file server in my home that's a G4 Mac mini running Debian Lenny, and it works flawlessly and indistinguishably from any x86-based box at the network level. However, I would never think of using it seriously in the role of a desktop system.

Second, PPC has always been a sort of "red-headed stepchild" in the Linux world. That doesn't mean there aren't dedicated groups out there, and again it doesn't mean nothing runs on it. Just understand that x86 has always enjoyed the best overall support (and the most love) of any supported hardware platform.

Third, Apple has never fully released documentation and specs for PPC systems. Consequentially, some stuff simply doesn't work, and may in fact never work. Other things, like sound or graphics acceleration, are fairly limited and oftentimes quirky in nature.

Forth, Apple has abandoned PPC, so any theoretical improvements that could have been made to the G4 or G5 or newer aren't being made, and likely will never be made. Not that this means as much for you since the hardware you've got is the hardware you've got, but nevertheless, you need to have reasonably modest expectations of what you're likely to achieve.

Now, that all being said, if you were talking about setting up a server (which you could repurpose a laptop for, but I wouldn't bother) let me be the very first to say for things such as samba and apache, a PPC-based Mac will work without issue.

Good luck and all the best...


Mike

---

### Post by ayenack on 2009-06-18
> **jangari said:**
> I'm intending to give this a go myself; about to acquire the same powerbook. The link to the PPC live CD images (for Jaunty) is [here]("http://cdimage.ubuntu.com/ports/releases/jaunty/release/"). 

Just give the live CD a go and see how it works before you install it. I've read that bluetooth can be a bit of a pain and the trackpad doesn't work too well, but I read that of Dapper Drake, so thinkgs may be much better now.

Let me know how it works.

Not sure it'll be possible to boot into a live CD with a Mac. They use boot camp not to sure how that'd work. But worth a try. I'll report back on how it goes when the lappy gets here.

Going to have to talk to a mate of a mate who's an IT Mac hardware manager. For info on the whole Apple Mac shebang. Do a bit more research online and in the forums also.

---

### Post by tgalati4 on 2009-06-18
An alternative strategy is to put Tiger on it.  Install Desktop Manager, X Windows, Fink.  That gives you a solid OS with all your hardware working.  With X, you can run 90% of FOSS.  You can also compile source for those packages not in Fink.

You can remote log into your Ubuntu machines with a full desktop as well.  Some FOSS programs have been rewritten for OS X.  Camino is a decent browser, based on mozilla code.

I've been using this setup for years.

---

### Post by ayenack on 2009-06-18
> **tgalati4 said:**
> An alternative strategy is to put Tiger on it.  Install Desktop Manager, X Windows, Fink.  That gives you a solid OS with all your hardware working.  With X, you can run 90% of FOSS.  You can also compile source for those packages not in Fink.

You can remote log into your Ubuntu machines with a full desktop as well.  Some FOSS programs have been rewritten for OS X.  Camino is a decent browser, based on mozilla code.

I've been using this setup for years.

Thanks for that tgalati4. That's really helpful and I'll look in to it for sure.

It'll have Tiger OS X 10.5.? fully updated with a load of software on it as well (when it finally gets here) so it'll be ready to go which ever way I decide to go.

---

### Post by tgalati4 on 2009-06-18
G4's are kind of pokey with Tiger 10.4.11.  The OS has gained bloat, but there are ways to slim it down, so it runs better on older hardware.  1.25 GB is OK.  I rarely swap with that amount.  You might be able to overclock video.  Mine's running at 110%.  Don't forget iScroll for 2-finger forum browsing.

---

### Post by ayenack on 2009-06-20
> **tgalati4 said:**
> G4's are kind of pokey with Tiger 10.4.11.  The OS has gained bloat, but there are ways to slim it down, so it runs better on older hardware.  1.25 GB is OK.  I rarely swap with that amount.  You might be able to overclock video.  Mine's running at 110%.  Don't forget iScroll for 2-finger forum browsing.

Thanks again. iScroll seems interesting.

---

