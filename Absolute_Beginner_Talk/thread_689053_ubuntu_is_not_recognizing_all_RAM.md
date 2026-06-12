---
title: "ubuntu is not recognizing all RAM"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by hhhhhx on 2008-02-06
hello everybody,
      i've recently built a computer and installed 4 gig's of RAM.  When i boot into the BIOS all 4 gig's are recognized. But when i boot tinto ubuntu or vista only 2.7 gb is recognized.

thx in advance.
               xhhux

---

### Post by lswest on 2008-02-06
i know this may seem a silly question, but are you using the 64 bit Ubuntu?  Otherwise i don't think the 32 bit supports 4GB of RAM

---

### Post by hhhhhx on 2008-02-06
> **lswest said:**
> i know this may seem a silly question, but are you using the 64 bit Ubuntu?  Otherwise i don't think the 32 bit supports 4GB of RAM

32 bit, but 32 bit suppports a max of 4 gig, and 64bit supports a max of 8 gig.

---

### Post by PeterJS on 2008-02-06
32 bit software only supports a maximum of 3.7 gigs of combined system and video RAM. I'd bet you've got a video card(s) with 1 gig of RAM taking up the remainder of that capacity.

64 bit can actually address up to 16 exobytes.

---

### Post by hhhhhx on 2008-02-06
no, my vid card is only 512MB, so i should be able to get 3.2 gb

---

### Post by bwtranch on 2008-02-06
Really? Unix only supports 4 Gigs? That's the first time i've ever heard that.

---

### Post by PeterJS on 2008-02-06
> **bwtranch said:**
> Really? Unix only supports 4 Gigs? That's the first time i've ever heard that.

Unix (software) can address as much memory as the hardware can support. 32 bit hardware by definition can not address more than 3.7 gigs of RAM, doesn't matter what's on top of it, Unix or Windows, no amount of software is going to over come that fundamental limit of 32 bit architectures.

---

### Post by hhhhhx on 2008-02-06
so should i give 64bit a try?

---

### Post by PeterJS on 2008-02-06
Try a 64bit live CD, if it works and finds all your RAM, then it would probably be worth installing.

---

### Post by hhhhhx on 2008-02-06
> **PeterJS said:**
> Try a 64bit live CD, if it works and finds all your RAM, then it would probably be worth installing.
cant use live cd's for some reason they wont boot

---

### Post by yaknowwat on 2008-02-06
All I can say is.

64 bit linux or big mem kernel 32 bit

at the moment the problem with 64bit is simple.
No 64 bit flash so you'd need to use a 32 bit internet browser or the supposedly glitchy ndiswrapper.
Also no real good 64 bit JAVA web browser support again solvable if you install a 32bit web browser.

big mem kernel is like a hack to keep using a 32 bit OS, I'm unsure how stable it is.  I'm pretty sure even with the big mem kernel your still limited with the 4 GiB limit, its just it uses linux architecture that likes to separate processes and allows you to run multiple processes that are limited by 4GiB each.

---

### Post by bwtranch on 2008-02-06
Gee, OK, Peter JS. That's why I get on the forum, is to learn something. You obviously know what you are talking about. I had just never heard about that. I will do some more checking into this as time goes on, that would become a serious limitation.

---

### Post by PeterJS on 2008-02-06
Sorry, didn't mean to come across as harsh, my bad.

---

### Post by scheuri on 2008-02-06
1) 32bit should be able to see and address (theoretically) about 4 GB of RAM. 64bit can see and adress more....

2) 32bit CAN address more than 4 GB using help from softare (PAE) which is able to map the RAM over 4 GB. HOWEVER using this means a DECREASE of performance and is usually only used if necessary and having the need of 32bit Software running with quite a lot of RAM.

3) VideoRAM and RAM for your "processor" on your motherboard has NOTHING to do with each other (concerning adding towards the 32bit limit that is)

4) 32bit should be able to address approx. 3.7 GB of your RAM without any troubles (using the standard kernel shipped with ubuntu). If that is NOT the case, I suggest you do a memtest!

You will "lose" approx. 300 MB of your RAM when using 32bit Kernel and Software. However, I doubt that is much of an issue.

Cheers
Stefan

---

### Post by zabien1970 on 2008-02-06
After reading this I'm left wondering what you need all that ram for? On my laptop I only have 1g of ram and generally use only 2/3 to 3/4 of it.   Even if it was all recognized what are you running that would need that much? If you don't currently need it I would run it as it is and as 64 bit becomes more standard and supported upgrade then.

---

### Post by hhhhhx on 2008-02-06
> **scheuri said:**
> 1) 32bit should be able to see and address (theoretically) about 4 GB of RAM. 64bit can see and adress more....

2) 32bit CAN address more than 4 GB using help from softare (PAE) which is able to map the RAM over 4 GB. HOWEVER using this means a DECREASE of performance and is usually only used if necessary and having the need of 32bit Software running with quite a lot of RAM.

3) VideoRAM and RAM for your "processor" on your motherboard has NOTHING to do with each other (concerning adding towards the 32bit limit that is)

4) 32bit should be able to address approx. 3.7 GB of your RAM without any troubles (using the standard kernel shipped with ubuntu). If that is NOT the case, I suggest you do a memtest!

You will "lose" approx. 300 MB of your RAM when using 32bit Kernel and Software. However, I doubt that is much of an issue.

Cheers
Stefan

so,.. how come i can only use 2.7 GB? i ran a memtest and got no errors, also my bios recognizes all 4 GB's of ram

---

### Post by Keks01 on 2008-02-06
your processor can address 4294967296 bytes (4GB) of memory. i.e. that is the maximal size of a pointer in 32 bit systems. Of course, a lot of these will be used by the processor for other things, that have nothing to do with memory addressing. Because of this it is normal that all 4GB of memory aren't addressed. 64 bit systems can store pointers up to 2^64 bytes, so 64bit OS is your best option ;)

---

### Post by Truin on 2008-02-06
Actually PAE is a a cpu-feature which must enabled from kernel not a basic software that you can "sudo apt-get install pae".
I haven't tested PAE enabling since it requires kernel compiling or pre-compiled kernel which at least I didn't find from my repos and I also have a modest 1 GB of RAM.
About the performance decrease PAE causes. Again I havent tested it but I doubt that it would cause DECREASE rather than small performance drop since it isn't anything like complex algorithm instead it's a rather simple memory address size increase from 32-bits to 36-bits
Read more: [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

Edit: Searched for the cpu hit. It seems that it's around 3-6%. Is it too much of a performance drop? It's about balancing between cpu hit and memory gain, I probably would take the cpu hit so that I could make use of all of my hw.
Here's the source where from I read about that performance loss 
[http://www.spack.org/wiki/LinuxRamLimits](http://www.spack.org/wiki/LinuxRamLimits)

---

