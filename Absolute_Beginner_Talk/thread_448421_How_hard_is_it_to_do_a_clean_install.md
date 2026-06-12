---
title: "How hard is it to do a clean install?"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by trishacupra on 2007-05-19
Hi,

I installed (K)Ubuntu a few weeks ago. I really love it, and have hardly used my dual-boot for Windows at all.

I have an external hard drive for my laptop that I divided into a few partitions. I have Windows installed on my laptop's internal hard drive, and GRUB is on the external drive.

I haven't used my home directory much - I've been saving my data on separate partitions on the external hard drive.

I've been modifying Ubuntu a lot, and haven't been keeping track of what I've done. I feel like it's gotten pretty messy, and I'd like to start over without losing my data.

Here is how my external hard drive is partitioned (attached).

How difficult would it be to just install Ubuntu on the boot partition again? What are the steps involved?

(It's not really a true dual-boot situation, because my BIOS boot order is set up to boot from the external drive first, if it's connected).

By the way, I think I didn't make the boot partition big enough - I just noticed I'm using almost all of it up. How big should it really be, and what are my options for moving it/ resizing it with it sandwiched in there?

---

### Post by AAM on 2007-05-19
Hi trishcupra!

you should be able to do a clean install the same way as before. I would make a few suggestions.

Back up your data first!

if you have a large media file collection use the XFS file system rather than ext3 (apparently better for large files)

Your root directory at 9+GB is large enough. The first install is ~1.5-2GB so there is a lot of excess.

If you have installed stuff, go through the menu with pencil and paper ready and record all the non-native options now there. In future keep a notebook with your additional installs and more importantly any hoops you had to jump through to get things to work.

Some particular reason for not killing off XP?

---

### Post by mikewhatever on 2007-05-19
At the partitioning stage, select manual, format / and swap, then remount them, and the other partitions if needed. This will erase all data on the / partition, so move all you want to keep from your home directory.

---

### Post by trishacupra on 2007-05-19
I'd love to ditch Win XP completely, but there are a couple of reasons why I'm reluctant to totally ditch it:

1. I do freelance graphic design and I need to use Photoshop. I don't have enough spare time to learn Gimp properly, and I have a whole lot of Photoshop actions that I can't use with Gimp anyway. I've been using Photoshop 7 with Crossover Office, but it's really not the same. Haven't tried VMware or Virtualbox - I'm not even sure how that works. But if it allows me to run Photoshop CS2 and the like fairly well, then I'd do it.

2. The WInXP that came with my laptop when I bought it last year is actually a legal copy. I have a serial number on the bottom of my laptop. I don't want to lose something I paid money for. (see next reason)

3. I didn't get an install CD with my laptop, just a recovery partition and I had to make system recovery discs - there are 10 CD's would you believe, and I don't even know if they burned properly.

4. As a web designer, I need to see how my sites work on Windows with IE and Firefox.

Would Virtualbox/VMware or whatever it's called allow me to run my legal Windows XP within Ubuntu, or how does that work?

Ideally, I'd love to put Ubuntu on my laptop's internal hard drive. Damn Photoshop - I really do need it.

Hey, that gives me an alternative - if I can wipe my internal hard drive with Windows but still be able to use Windows somehow, then I can do a clean install on my internal drive and then just wipe the boot and swap partitions on my external drive...

How does it work? What's best?

---

### Post by dilb on 2007-05-19
> **trishacupra said:**
> 
4. As a web designer, I need to see how my sites work on Windows with IE and Firefox.


You might want to look at [IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page")

I'm afraid I can't help with your other issues. I would suggest sticking with Windows is probably the easiest solution and just use Ubuntu for everything else, but that's up to you.

---

### Post by mikewhatever on 2007-05-19
> Would Virtualbox/VMware or whatever it's called allow me to run my legal Windows XP within Ubuntu, or how does that work?
VM uses part of the computer RAM and CPU to run, so you most probably do not want it for your work with photoshop. Occasional internet browsing or text editing is OK though.

---

### Post by kinematic on 2007-05-19
> **trishacupra said:**
> How difficult would it be to just install Ubuntu on the boot partition again? What are the steps involved?

what makes you think it will be any different from installing it the first time?
you managed to install it the first time didn't you!

---

### Post by trishacupra on 2007-05-20
I think I'll reinstall Windows clean on my laptop's hard drive, and use the rest of the remaining space for my Ubuntu boot. At the moment I couldn't do this because Windows spread files all over the hard drive and numerous defrags wouldn't make enough continuous space to install Ubuntu, would you believe. (Of course you would - typical M$ rubbish.)

---

### Post by trishacupra on 2007-05-20
> **kinematic said:**
> what makes you think it will be any different from installing it the first time?
you managed to install it the first time didn't you!

I muddled through it the first time, and it didn't go as I planned.	:roll:

---

