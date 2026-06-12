---
title: "CPU speed test, unnecessary swap memory usage"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by findik1 on 2007-04-09
Hi 

I got used computer dell desktop optiplex, p4 HT 3.2 ghz to mainly use for scientific computation, MATLAB. I erased winxp, put first win2000, and hen fresh ubuntu 6.10. 
I tested its speed with matlab bench command. It was way slow, it gave similar to pentium 4 2 GHz work. Since I am nor familiar with HT, I disabled double CPU, so that when matlab works all CPU should concentrate on matlab. Then I typed bench(this is a automatic program to test howlong does it take for your computer to finish some scientific process, such as matrix inversion, plotting and so on). Then I saw that I did not see ANY improvement at all. 
Is it because I erased winxp and I should fist install some drivers for chipset?
Second problem is with memory. It had 1256MB memory but when I opened a pdf file with evince I saw that computer already started using swap memory!(see attachment). Maybe they put wrong memory to this computer. Its is DDR2 memory but maybe chipset or frequency does not match?
After that I closed ll the programs, I see that t still uses its swap memory. and it uses its main memory of 126 MB of 1.2GB (read from system monitor)

Any suggestion to improve performance would be very valuable. Again I want to stress that there is no other files installed, just matlab, so there are lots of space in HD, everything is fresh, so performance is expected to be far better than this.
best,
findik

---

### Post by dbbolton on 2007-04-10
i'm not sure about your processor issue -- it seems to be doing pretty well if it peaked at 10% -- but the swap use is completely normal, although i've never a swap partition that large.

---

### Post by findik1 on 2007-04-11
> **dbbolton said:**
> i'm not sure about your processor issue -- it seems to be doing pretty well if it peaked at 10% -- but the swap use is completely normal, although i've never a swap partition that large.

thanks for the response!
I put 8GB as swap as 2 times of memory of computer (thinking in the future I may increase the memory).

---

### Post by igknighted on 2007-04-11
> **findik1 said:**
> thanks for the response!
I put 8GB as swap as 2 times of memory of computer (thinking in the future I may increase the memory).

2x the memory was an old rule... The swap is only used when memory is used up.  And you will never use up 1.2GB.  I would NEVER do a swap size of over 1gb, its a waste.

---

### Post by findik1 on 2007-04-12
> **igknighted said:**
> 2x the memory was an old rule... The swap is only used when memory is used up.  And you will never use up 1.2GB.  I would NEVER do a swap size of over 1gb, its a waste.

OK I see. Then I should reduce it. How do you answer then: although I have lots of memory in my computer (1.2 GB), ubuntu started using swap (see above attachment). Is there stg wrong?

---

### Post by dbbolton on 2007-04-12
typically, there is a ratio of mem use to swap use. i think it's approximately 7:3

---

