---
title: "ThinkPad i1472"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by CodeHead on 2007-03-07
All:

I did a low-level format on my hard drive, so that I would have a clean slate, and removed all XP disk partions.

I downloaded Xbuntu 6.06 LTS and burned it onto a CD (on my other PC, which is running XP). When I try to install it from this CD, I'm getting the following error message, a few minutes after the install starts:

/bin/sh: can't access tty; job control turned off

[ 92.254954] irq 15: nobody cared (try booting with the "irqpoll" option)

[ 92.019275] handlers:

[ 92.030199] [<c02521a0>] (ide_intro+0x0/0x200)

[ 92.041473] Disabling IRQ #15

Then the four numbered lines above keep repeating themselves about once per second.

Any ideas of what is causing this problem?  How do I boot with the "irqpoll" option and can I do this from a bootable CD?

Thanks,

:guitar:

---

### Post by watson540 on 2007-03-08
yes you can. when you boot from the cd , when the menu pops up hit f6, then type irqpoll and hit enter :) good luck

---

