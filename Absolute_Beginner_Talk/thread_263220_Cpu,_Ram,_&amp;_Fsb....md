---
title: "Cpu, Ram, &amp; Fsb..."
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by ReaderRat on 2006-09-22
I did a memory check as I was installing Ubuntu (which was OK), but in the words/numbers on screen I saw FSB - 200MHz.  I have a 3.2 GHz P D Dual Core CPU and 533MHz RAM (wish I had 800 MHz RAM). Is the Front Side Bus running @ 200 MHz, and, if so, what is wrong or what else determines FSB rate? The mobo & CPU are supposed to support an 800 MHz FSB. Thank you for being there when I need someone to help....

---

### Post by someonedumb on 2006-09-22
Oh a hardware question!
DDR memory specs are not for the actual speed the memory is running it, it is for *effective* speed. For example, my memory is running at 266MHZ(DDR), but its really only running at 133 MHZ.

And I believe that 800MHz would be DDR2, running at an actual 200MHz(DDR doubles the effective memory speed, and DDR2 quadruples it)

In your case, it sounds like you overclocked your 133MHZ (533DDR2) to 200MHZ(800DDR2)
If you are unstable at all that is why... but if not, then grats on 800MHZ FSB/Memory

---

### Post by WalmartSniperLX on 2006-09-22
Memory right now is DDR memory, or Double Data Rate. It has a maximum transfer rate of 400, on two lanes added together. Theres actually 200mhz active but its running double the lanes of normal SDRAM.

So that fsb rating is your memory (so if you have ddr1 its half. DDR2 has some weird forumula 

In other words, your memory speed should come up half (for ddr400) the speed the memory is rated. lol I hope that makes sense.

---

### Post by WalmartSniperLX on 2006-09-22
> **someonedumb said:**
> Oh a hardware question!
DDR memory specs are not for the actual speed the memory is running it, it is for *effective* speed. For example, my memory is running at 266MHZ(DDR), but its really only running at 133 MHZ.

And I believe that 800MHz would be DDR2, running at an actual 200MHz(DDR doubles the effective memory speed, and DDR2 quadruples it)

In your case, it sounds like you overclocked your 133MHZ (533DDR2) to 200MHZ(800DDR2)
If you are unstable at all that is why... but if not, then grats on 800MHZ FSB/Memory

I think this is a better way to look at it :P

---

### Post by ReaderRat on 2006-09-22
I don't know anything about overclocking. I got the parts, put the box together, turned it on, and it ran like this. Will overclocking damage anything?
BTW< I have DDR2 memory.

---

### Post by furiousV on 2006-09-22
You'r CPU *External Clock* is running at 200MHz, but the *Effective Front Side Bus* is running at 800MHz, which is actually 4x what it is really ticking at.

For your DDR memory, as was mentioned, is actually ticking at 266MHz, but as its DDR it is doubled, as data is process as the cycle is going up AND down (think of a Sin/Cosine graph in Maths). That gives you the 533MHz.

It confused me at first when I had a P4 2.8 Prescott (800MHz FSB) and DDR400 memory . . . . wait . . . I'm still confused :-$

---

