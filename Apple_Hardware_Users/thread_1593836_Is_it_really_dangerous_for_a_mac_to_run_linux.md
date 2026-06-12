---
title: "Is it really dangerous for a mac to run linux?"
date: 2010-10-11
forum: Apple Hardware Users
---

### Post by troubleshot on 2010-10-11
I have an Imac and as I was on the irc for mac I was told that:

It is *strongly* recommended that you do not run any linux natively on any Core-equipped Mac -- to do so will result in premature CPU death.

That statement scares me. So how have you guys managed with this?

---

### Post by srs5694 on 2010-10-11
This topic came up a couple of months ago. IIRC, nobody could post anything more authoritative than "my cousin's friend's brother works in an Apple Store, and he said he thought he heard somewhere that Linux might cause hardware problems."

In other words, it's [FUD.](http://en.wikipedia.org/wiki/Fear,_uncertainty_and_doubt)

---

### Post by troubleshot on 2010-10-11
But what incentive do they have for using fud? They had what seemed to me the layman a very good cause: 

Apple use a brain-dead custom power management chip that forces the host OS to micromanage everything; no linux distro has full SMC support, especially a complete absence of Vcore control. The result is that the CPU is left in a permanently over-volted state. The newer the Core processor, the faster it will succumb to 'overclocker's cancer.'

Do not get me wrong. I am not here for fud, I love linux and that is why this worries me.

---

### Post by david_edmundson on 2010-10-11
Maybe not FUD, but second-guessing and chinese whispers could well be at play here.

I've been using Linux exclusively on my macbook for 3+ years with no trouble at all (with the processor).

My processor spends most of it's time with the clock underclocked down to 1Ghz, (it boosts when needed). I wouldn't be surprised if this doesn't adjust voltage too.

Thanks to tickless idle in Linux, the processor spends most it's time in C4 state - effectively powered off so a higher Vcore makes no difference.

I would like to see a real source on this. If you have any links/evidence please post it. Personally I find it unlikely that in the absence of an OS to manage it, the bios boosts itself past anything unsafe.


My Evidence:
Cpu voltage is controlled via EIST - this is fully supported by Linux. 
Source: [http://www.lesswatts.org/projects/processor-power/faq.php](http://www.lesswatts.org/projects/processor-power/faq.php)

---

### Post by troubleshot on 2010-10-11
I do not have any links or evidence and that is the reason I came here. I wanted to bounce this off you guys to see if you thought there was enough credibility to warrant concern.

---

### Post by tgalati4 on 2010-10-11
Try a used Thinkpad--runs linux well and it's as ugly as sin.

---

### Post by jamesey on 2010-10-12
ive been exclusively running ubuntu on my imac that I bought in march 2009. there's nothing wrong with it.

---

### Post by tpievila on 2010-10-12
Please google first. One of the first hits was this thread: [https://bbs.archlinux.org/viewtopic.php?pid=748111#p748111](https://bbs.archlinux.org/viewtopic.php?pid=748111#p748111)

---

