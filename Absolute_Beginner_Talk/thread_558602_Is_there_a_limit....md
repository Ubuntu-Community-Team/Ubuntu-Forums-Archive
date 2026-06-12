---
title: "Is there a limit..."
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by stevebakerj on 2007-09-24
to how much RAM *ubuntu can use?  e.g. XP will only use 3Gig

---

### Post by PmDematagoda on 2007-09-24
It all depends on whether you use either a 32 bit or 64 bit OS. If you run 32 bit Feisty, then you will only be able to use only about 3.2 Gb of RAM, like on your 32 bit Windows. But with 64 bit Feisty(or 64 bit Windows) you can use about 4 terabytes of RAM(VERY BIG:)).

---

### Post by mjwhitfield on 2007-09-24
> **PmDematagoda said:**
> It all depends on whether you use either a 32 bit or 64 bit OS. If you run 32 bit Feisty, then you will only be able to use only about 3.2 Gb of RAM, like on your 32 bit Windows. But with 64 bit Feisty(or 64 bit Windows) you can use about 4 terabytes of RAM(VERY BIG:)).QFT, it's a processor limit, not an OS limit.

---

### Post by PmDematagoda on 2007-09-24
> **mjwhitfield said:**
> QFT, it's a processor limit, not an OS limit.

Not at all. My processor is two years old and it supports 64bit, all the processors. etc. coming out these days support 64 bit. This means that the processors, mainboards, etc. support enormous amounts of RAM. It's only the problem with the OS if you can't get more than 3.2 GB RAM to be used, as you are using 32 bit not 64 bit.

Of course for people who have 32bit processors, then you are limited by the processor itself and you can't install a 64 bit OS. Sorry

---

### Post by stevebakerj on 2007-09-24
OK thanks I will d/l the amd64 .iso and test that.

---

### Post by PmDematagoda on 2007-09-24
How much RAM do you actually have? What's the processor and mainboard?

I could tell you if your PC supports (or needs) 64 bit.

---

### Post by stevebakerj on 2007-09-24
Ive just inherited it as a test setup.

Intel D950
8 GB RAM 4 * 2GB
Intel D975XBX2 MOBO

---

### Post by PmDematagoda on 2007-09-24
First off, I got to say that's an awesome PC. Having 8 Gb of RAM is something I've never heard of.

And since it is more advanced than my P4 HT CPU, 64 bit Ubuntu should be able to support 8 GB RAM like a breeze, and you definitely need 64 bit in order to use such a lot of RAM since in your case more than half of it would be wasted by a 32 bit system, also, with that amount you should expect Ubuntu 64bit to be really fast. :)

---

### Post by stevebakerj on 2007-09-24
I've burned the amd64 iso to disk now, so I will fire it up and see how it goes.

---

### Post by PmDematagoda on 2007-09-24
I would be interested to know how it goes.:)

One more thing, with that much of RAM, you most probably won't need a swap partition as it would be nothing but a waste of disk space.

---

### Post by LaRoza on 2007-09-24
> **PmDematagoda said:**
> 
One more thing, with that much of RAM, you most probably won't need a swap partition as it would be nothing but a waste of disk space.

Tell that to those who believe swap should be twice the size of RAM. :D

---

### Post by PmDematagoda on 2007-09-24
> **LaRoza said:**
> Tell that to those who believe swap should be twice the size of RAM. :D

Tell that to me:lolflag:, I have 1Gb RAM and a 2Gb Swap. I did it by accident after choosing the guided partition method, I'll have to be more careful when I install 64-bit Ubuntu.:-D

---

### Post by Dr Small on 2007-09-24
> **stevebakerj said:**
> Ive just inherited it as a test setup.

Intel D950
8 GB RAM 4 * 2GB
Intel D975XBX2 MOBO
Inherited a test setup ? O.o
Maybe you are a geek! :D

Dr Small

---

### Post by LaRoza on 2007-09-24
> **PmDematagoda said:**
> Tell that to me, I have 1Gb RAM and a 2Gb Swap. I did it by accident after choosing the guided partition method, I'll have to be more careful when I install 64-bit Ubuntu.:-D
Now I prepare disks with GParted LiveCD, then do a text install. Much more control.

---

### Post by PmDematagoda on 2007-09-24
> **LaRoza said:**
> Now I prepare disks with GParted LiveCD, then do a text install. Much more control.

Yes, I'm thinking of doing that myself. Of course, first time is not going to be perfect. But I've done partitioning before, with Norton Partition Magic.

---

