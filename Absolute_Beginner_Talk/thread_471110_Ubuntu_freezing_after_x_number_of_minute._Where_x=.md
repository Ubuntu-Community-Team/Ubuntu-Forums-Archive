---
title: "Ubuntu freezing after x number of minute. Where x=some random #.  Hardware problem?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by allthingsfixable on 2007-06-11
My installation of Ubuntu 6.06 Server edition continually freezes after a random amount of time varying from 5 minutes. I have reinstalled, reintalled again, installed Ubuntu desktop edition, and then reinstalled again. I've run diagnostics on my RAM, swapped out my RAM, and run diagnostics on my hard drives. And that's about all I know how to do.

Is there some way to determine what my computer is doing right before it decides to freeze?  It freezes no matter what I am running/doing at the time or if I am even using the computer. 

I can get more specs on my machine if anyone thinks they can help, however I am not at home at the moment.

Thanks!

---

### Post by leibowitz on 2007-06-11
Yep it could help to have more details about your Hardware.

If you want to know what it does before the freeze, try to open different logs ( like /var/log/messages )

---

### Post by DanN on 2007-06-18
I've had exactly the same situation.  I've just bought a new computer and put ubuntu studio on, but that failed during the install when it hard locked up, I retried but same thing happened (at a different spot), so I tried regular ubuntu, it installed, but had random hard lockups (and other weirdness).  I did a memory check and it showed errors in the memory so I swapped that out thinking, that must be the problem, but I'm still having problems (though perhaps less frequently), a memory check on the new memory shows it's clean too.

Does anybody know what other hardware might cause this kind of behaviour, of if it could possibly be a software issue?

My specific hardware is:
Intel e-6420 core 2 duo CPU
Gigabyte 965GM-DS2 mobo
2 Gigs corsair memory
320 gig seagate hd

---

### Post by leibowitz on 2007-06-18
It's probably linked to some hardware issue. 

But sometimes, like I had with a PCI Wireless card, a kernel module bug is the cause.

So it's hard to say, you must "track" the cause.

I had this while using a Beta, and it takes me two or three days to find out it was a driver issue. But in my case I was using an older ubuntu version on that computer just fine.

So you may try with another distribution, another version, and see if it's doing the same. It may help

---

