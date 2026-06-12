---
title: "FreeBSD tips"
date: 2009-01-24
forum: BSD
---

### Post by cardinals_fan on 2009-01-24
I've finally decided to move full-time to a BSD system.  I just love the stability and simplicity of the BSDs.  I've been a NetBSD user for about a year, both on my secondary box and in virtual machines.  However, I've decided to give FreeBSD a shot before settling on Net for my main machine.  Though I've used FreeBSD in the past, I never really felt like I utilized all its potential.

I downloaded FreeBSD 7.1 disk one last night.  In about 15 minutes I'm off to buy some CD-Rs.  When I return, I'm burning and installing FreeBSD.  Before I start, does anyone have any tips or suggestions?

---

### Post by JMJ_coder on 2009-01-24
Are you planning on primarily being a cli user or a X user?

---

### Post by cardinals_fan on 2009-01-24
> **JMJ_coder said:**
> Are you planning on primarily being a cli user or a X user?
X with lots of CLI apps.

---

### Post by JMJ_coder on 2009-01-24
> **cardinals_fan said:**
> X with lots of CLI apps.

In that case, I would suggest not skimping on the swap slice. X apps tend to be way more bloated then cli apps (you probably already new that).


Is there a particular area or feature in FreeBSD you want to explore?

---

### Post by JMJ_coder on 2009-01-24
I, too, downloaded the 7.1 DVD the other day. I don't necessarily intend to install it, but you never know when it might come in handy. I have the same with OpenBSD, which I might actually try, since I never have (last time I explored, they didn't offer an iso - and I was too inexperienced at the time to make one myself).

---

### Post by cardinals_fan on 2009-01-24
It's installed!  I pkg_added firefox3 and some other necessities.  The rum driver for my wireless adapter really is better on FreeBSD (the NetBSD version always gave me trouble).  Odd, since I think they were both ported from OpenBSD at one time.

Anyway, I really like this system so far.  I'm tackling Flash now...

---

### Post by JMJ_coder on 2009-01-24
> **cardinals_fan said:**
> It's installed!  I pkg_added firefox3 and some other necessities.  The rum driver for my wireless adapter really is better on FreeBSD (the NetBSD version always gave me trouble).  Odd, since I think they were both ported from OpenBSD at one time.

Anyway, I really like this system so far.  I'm tackling Flash now...

How bad was the firefox install? Binary or source or linux emulation? And how many dependencies did it have to install as well?

---

### Post by cardinals_fan on 2009-01-24
> **JMJ_coder said:**
> How bad was the firefox install? Binary or source or linux emulation? And how many dependencies did it have to install as well?
Binary.  I don't like source-based packaging and I won't emulate unless I have to.  It didn't have many dependencies, but I had already installed the whole X User package set.

---

### Post by Sorivenul on 2009-01-24
I'm here now. What do you want to know? ;)
Side note: I'm considering a switch to NetBSD or DragonFlyBSD, of all things.

---

### Post by cardinals_fan on 2009-01-25
> **Sorivenul said:**
> I'm here now. What do you want to know? ;)
Side note: I'm considering a switch to NetBSD or DragonFlyBSD, of all things.
I experimented with DragonFlyBSD 2.0 a couple weeks ago.  It is very cool (especially HAMMER), but I didn't see any real advantages for my desktop system.  It is pretty stable now.

NetBSD is, as always, awesome.

---

### Post by mips on 2009-01-25
I wish FreeBSD had a 64bit nvidia driver, I actually wish the same for all the other BSD's as well. It really is a nice OS.

---

