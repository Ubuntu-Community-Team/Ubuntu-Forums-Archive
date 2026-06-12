---
title: "memory question"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by rdsii64 on 2008-04-12
I currently run Ubuntu on a second hand machine to compliment my windows box. because it's dirt slow I have been looking for its replacement. What I found is a second had workstation class rig. ( dual 3 ghrz xenon processors, 6 gigs of ram, quadro fx 1400 agp graphics 4x 73gig 10,000 scsi hard drives) what I am wondering is whether or not a 32 bit Ubuntu os can address 6 gigs for ram. The reason I am asking is that believe these xenon cpu's are  single core32 bit as apposed to the newer multi core 64 bit.
I almost forgot, all that for less than $1,000.00 US

---

### Post by schnauzer93 on 2008-04-12
I don't think it's possible for a 32-bit OS to address more than 4 gigs of RAM. But I could be wrong.

---

### Post by hyper_ch on 2008-04-12
it is, with pae...

so I think if the motherboard supports more than 4gb then it's pae and then it should also work in ubuntu 32-bit... but I don't know for sure.

---

### Post by rdsii64 on 2008-04-12
> **hyper_ch said:**
> it is, with pae...

so I think if the motherboard supports more than 4gb then it's pae and then it should also work in ubuntu 32-bit... but I don't know for sure.
Could you explain what you mean by pae

---

### Post by hyper_ch on 2008-04-12
> **rdsii64 said:**
> Could you explain what you mean by pae

have you tried figuring out what PAE could be?

---

### Post by phread59 on 2008-04-12
32 bit porgrams as far as I know are capped at 4GB.  With a 64 op system you are good to 128GB.  The board may be able to support the 6GB but the OP system will only recognize and use 4.  There is a 64 bit Ubuntu application.  It will be able to access the whole 6GB.  It's up to you to use as you see fit.  Either will work just fine.  Only concern I have is the dual processors.  Not sure if a non server software package will access them both.  Not sure on that account.  Only way to find out is load it up and try it.  Good luck.

Mark Shuman

---

### Post by hyper_ch on 2008-04-12
> **phread59 said:**
> 32 bit porgrams as far as I know are capped at 4GB.
Without PAE --> yes... with PAE --> no

> **phread59 said:**
>  With a 64 op system you are good to 128GB.
Nope, you are good to 2^64 bytes

---

### Post by Bendrx on 2008-04-12
Physical Address Extention. It's an Intel feature that allows 32bit OSs to use up to 64GB with a performance hit of course. Anyways it's part of the kernel, I'm not sure if there is a precompiled kernel you could use or upgrade option, I know little of the way of the Kernel. All hail the great Kernel! Anyways if you give up some CPU cycles you can use all 6 Gigs. I also think you'll need a SMP (dual processor support)  kernal, don't know but the standard might support it already.

---

