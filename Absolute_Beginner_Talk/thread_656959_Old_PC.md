---
title: "Old PC"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by sundeniro on 2008-01-03
Hi all

Forgive the naivety of my question but io have never used linux/ubuntu before.

I have an old win 95 PC in the garage, pentium 300mhz 64mb RAM (it was orogionally bought in about 1996)that is obviously totally useless on any useful version of windows.

A friend told me he would consider putting a simple version of Linux on it as It would just be used as a spare PC for mainly surfing.

Is this PC likely to work with Linux/ubuntu or would I just be wasting my time, If I decided to build a PC from scratch with the intention of running Ubuntu, mainly for surfing and document imaging and running OPen Office what would be minimum Spec you guys would recomend, keeping it as cheap as possibl?

Many Thanks in Advance for any answers

---

### Post by LaRoza on 2008-01-03
That computer will be able to run modern versions of Linux.

See the Other OS Talk subforum, and review the sticky on OS's for old computers. [http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

I'd vote for Puppy or DSL or [http://jinx-linux.sourceforge.net/](http://jinx-linux.sourceforge.net/)

---

### Post by kestrel1 on 2008-01-03
I would go with Puppy Linux. Very small footprint on HDD & works very well.

---

### Post by sundeniro on 2008-01-03
Many thanks

For the quick reply - I have heard of puppy linux before as being great low spec systems how easy to us is it for a complete novice with Linux although I am quite IT literate.

any other suggestions etc?

---

### Post by LaRoza on 2008-01-03
> **sundeniro said:**
> Many thanks

For the quick reply - I have heard of puppy linux before as being great low spec systems how easy to us is it for a complete novice with Linux although I am quite IT literate.

any other suggestions etc?

Puppy is very easy to use. The sticky I mentioned had a large list which is worth looking into.

[http://www.puppylinux.org/user/photogallery.php?album=3](http://www.puppylinux.org/user/photogallery.php?album=3) There are some screenshots.

---

### Post by ugm6hr on 2008-01-03
Ubuntu will be unbearable on that.  Even PuppyLinux will be a bit slow, I suspect.

|I would recommend DSL (damnsmalllinux) which I have installed on lesser machines.  DeliLinux is supposed to be designed for machines of that calibre, but I've never used it.

---

### Post by kestrel1 on 2008-01-03
I found Puppy very easy to use, but as mentioned above, you may find it a bit slow on a machine with that spec. Adding more memory may help, but only if you have some kicking around that is compatable with that system.

---

### Post by sundeniro on 2008-01-03
the memory is already maxed out at 64Mb it used to be a relatives and I upped the memory for her about 5 years ago and that was as much as the board would take!

I did read through the suggested thread but the emphasis seemed to be on the size of the program for delivery media rather than for the running of it.

I suppose I could always try puppy and take it off if it's too slow!

---

### Post by kestrel1 on 2008-01-03
What you could do is try one of the older versions of Puppy, they are available for download here:
[http://www.puppylinux.org/user/downloads.php?cat_id=1](http://www.puppylinux.org/user/downloads.php?cat_id=1)

---

### Post by louieb on 2008-01-03
I have a P2-400mHz 384MB ram I bought in 97 (with a P2-166mHz and 64MB ram) - its primary use today is a sandbox. Just seeing what works and what doesn't. 

Check the specs. Bet it uses PC100 or PC133 memory and has a P2 CPU. If so RAM is cheep on eBay.  For 10-20 bucks or so probably can bump it up to 256 or 384 MB memory.  - Enough to run  most distros. and the lighter ones  such as DSL or Puppy or PCFluxboxOS will run pretty well.

---

### Post by ugm6hr on 2008-01-03
> **kestrel1 said:**
> What you could do is try one of the older versions of Puppy, they are available for download here:
[http://www.puppylinux.org/user/downloads.php?cat_id=1](http://www.puppylinux.org/user/downloads.php?cat_id=1)

Indeed, the problem is predominantly that the Linux 2.6 kernel is probably going to struggle on that computer.  Puppy 1.x was a 2.4 kernel (I never used it though), and is no longer being developed or supported, so I think it is probably not your best option.

Similarly, DSL and DeliLinux are 2.4-based *modern* distros.  So they are probably better.  Have a look yourself:
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)
[http://www.delilinux.de/](http://www.delilinux.de/)

---

### Post by sundeniro on 2008-01-03
To complicate things a little further this PC connects to thw web using a wireless dongle at the moment and my intention would be to maintain this, I should have mentioned this earlier I know.

at the moment my plan is to try puppy and if i think it drags switch to dsl, anyone think i'm being foolish please feel free to tell me.

---

### Post by ugm6hr on 2008-01-03
> **sundeniro said:**
> To complicate things a little further this PC connects to thw web using a wireless dongle at the moment and my intention would be to maintain this, I should have mentioned this earlier I know.

at the moment my plan is to try puppy and if i think it drags switch to dsl, anyone think i'm being foolish please feel free to tell me.

That sounds like a reasonable plan.  How au fait are you with Linux?

The reason I ask is that Puppy will probably struggle to install with 64MB RAM, unless you have a swap partition.

Therefore, it makes sense to boot with DSL, use the command *parted* to run the partitioning program, create an appropriate ext3 (the rest of the disk) and swap partition (about 96-128MB).

Then boot from the Puppy CD and try to install.

As for a USB wifi dongle.... Puppy has a good wifi configuration program (that includes ndiswrapper - so is better than Ubuntu!), whereas DSL has none (I think).  DSL will require a bit of work (unless you are very lucky).

---

### Post by sundeniro on 2008-01-03
I have no experience of Linux at all:(

But a high IQ and lots of patience:)

---

### Post by Lostincyberspace on 2008-01-03
You might even try xubuntu on it, if you slim it down a bit it should run okay just give it about 512MB for swap.

---

### Post by sleepingdragon on 2008-01-03
I would go for DSL on those specs. They've released a newer version - v4.2.2 - which has a better interface and runs nicely. There are some wireless tools available, so you might be in luck with that wireless connection of yours! There is an older version of OpenOffice available in DSL, so you should be good on ODF compatibility too.

---

### Post by ugm6hr on 2008-01-03
> **sundeniro said:**
> I have no experience of Linux at all:(

But a high IQ and lots of patience:)

No worries.  Thats exactly what's required for fun with LInux!  My first Linux experience (under a year ago) was DSL, purely because I wanted to resurrect a similarly ancient (in fact more so - 48MB RAM, P2 processor - can't remember speed - now donated to home-schooled student) computer.  It was pretty good with DSL3.x, but unusable with Puppy2.x.

EDIT: This thread just made me look into DSL again, and it now uses JWM as default on 4.2 (instead of fluxbox), and looks pretty nifty:

[IMG]http://www.linuxseekers.com/images/stories/screenshots-of-damn-small-linux-4.2/new-desktop-for-dsl42.png[/IMG]

It also appears to have some wifi tools too:
[IMG]http://www.linuxseekers.com/images/stories/screenshots-of-damn-small-linux-4.2/right-click-on-the-desktop-to-get-the-MAIN-MENU.png[/IMG]
Screenshots from:[http://www.linuxseekers.com/content/view/223/1/](http://www.linuxseekers.com/content/view/223/1/)

---

