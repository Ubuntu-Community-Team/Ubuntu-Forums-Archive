---
title: "input freeze with new RAM"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by scradock on 2007-12-28
I'm running Gutsy 64-bit on an AMD single-core (hp pavilion zv6007us), and getting a freeze-up after adding extra RAM. I don't have any bleeding-edge video drivers - the 8.37.6 fglrx as supplied by Ubuntu. Not using Compiz. The machine only freezes with 64-bit Gutsy - seems to run fine with 32-bit Gutsy or Hardy.

The freeze happens soon after boot - anything from 2 minutes to 20 minutes, so it's probably not a memory leak. System Monitor shows low cpu usage, low memory usage, no creep upwards.

I had 2 256MB sodimm boards, and replaced one with a new Patriot 1GB. The other is buried deep in the guts of the machine, so I don't want to bother it. Memtest says the RAM is all good. Putting the old 256MB module back seems to fix the problem.

Is there any chance that this is something OTHER THAN a faulty RAM chip? I can take it back and get another one, but I don't want to do that if it isn't actually the new RAM.

---

### Post by thekylehome@gmail.com on 2007-12-28
It could be that your RAM modules won't support that size. (1GB) because if you had two 256MBs, then it probably won't support 1GB... 
Also, did you make SURE that the new stick has the EXACT same specs as the old? if not, that could cause the 64bit version not to like it because it wouldn't match up with the hardware...

just some of my thoughts-----

Hope you get it figured out!

---

### Post by scradock on 2007-12-28
I don't think it's a machine limitation - the manufacturer's specs say up to 2GB total, which has to be 2 x 1GB. If the Gutsy 64-bit modules won't handle more than 2GB I would be very surprised. The only worry I had was that having such different amounts in the two slots would be a problem, but the 32-bit Ubuntus don't seem to mind at all. Nor does WinXP, for that matter.

The PC2700 DDR 200-pin sodimm doesn't have a lot of options, as far as I know. The speed rating is higher on the new one, which should not be a problem, should it?

Anyone else got some ideas?

---

### Post by scradock on 2007-12-28
There's a thread over on the 64-bit forum about this sort of thing. It happens ONLY with 64-bit Ubuntu, ONLY with lots of RAM. The theory being proposed is that with lots of RAM the video driver thinks it can write stuff anywhere above a certain point, but other drivers think they can too. When there's a collision something stops working. Sounds kind of elementary - the sort of thing that an OS more advanced than DOS ought to prevent, doesn't it?

I guess I should just stick to 32-bit if I want stability......

---

### Post by vdubbus77 on 2007-12-28
I had a similar problem when I upgraded on a Gateway. A bios update helped with my problem. YMMV.

---

