---
title: "[SOLVED] Howto find out the Graficcard RAM?"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by shareMenaPeace on 2008-01-09
Good Morning, 
i run a ATI xpress 2300 and everythign just runs smooth, i just realized a little oddness with my grafic card ram.

In Ati Catalyst Settings Tool it only states 64 mb of ram, i know that the basic model of my asus notebook has this specification but i bought 1 with 128 ram.

Than when i run virtualbox, it let me choose to share with the virtual machine 128 ram, so how can i find out about the ram on my grafic chip exactly?

And has the ATI Control Center Display of Ram any influence on my performance?
Can i change the setting with the ati config tool?

Thanx for ideas and help,

Cheers

---

### Post by mcduck on 2008-01-09
ATI xpress 2300 uses what Ati calls 'HyperMemory', which means that it has some RAM of it's own, and the rest it takes from your system memory.

So in your case your graphics card has only 64MB of dedicated graphics memory, and the Windows driver then steals additional 64MB  from your computer's RAM to increase that into 128MB.

Virtualbox is talking about your system memory, not graphics memory.

---

### Post by shareMenaPeace on 2008-01-09
Thanks mcduck!
hmm i thinkj i can and have to life with this fact :D ... that the ati card is takeing additional 64mb ram is not so big problem as i have 2 gb.
Well but i should better had bought the other notebook with 256 ram :D (more expensive)

Cheers

:popcorn:

---

