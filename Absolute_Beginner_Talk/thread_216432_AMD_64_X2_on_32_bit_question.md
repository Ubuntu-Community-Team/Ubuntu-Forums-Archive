---
title: "AMD 64 X2 on 32 bit question"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by BIZKeT on 2006-07-15
I have found where to check the system useage stats and, to my untrained eye, it looks like Ubuntu Dapper 32 bit is only using one core. Is there a way I can find out if it is using both cores? The next question would then be, if it is not how would I get it to do so?

This community has been great. I got my chipset drivers installed finally, I have learned to get around with Synaptic, and I can get Ubuntu to read the files off my Nomad Zen Xtra (altho I can't stream from it), all because of this community. You guys are fantastic! As soon as I can figure out a way to give Transgaming money that doesn't require a credit or debit card I will be wiping my Windows drive for good!

BIZKeT

---

### Post by BIZKeT on 2006-07-17
Can anyone give me an idea on this please?

BIZKeT

---

### Post by MrHorus on 2006-07-17
You are most likely running a stock i386 kernel.

If you install an AMD64 kernel then you will most likely see both cores and get a performance boost from the additional registers and what not, but unfortunatly I don't know offhand what kernal image you will need.

I have no doubt that SOMEONE here will know tho :)

---

### Post by BIZKeT on 2006-07-17
> **MrHorus said:**
> You are most likely running a stock i386 kernel.

If you install an AMD64 kernel then you will most likely see both cores and get a performance boost from the additional registers and what not, but unfortunatly I don't know offhand what kernal image you will need.

I have no doubt that SOMEONE here will know tho :)

I don't want to run with the 64bit OS. I am just getting started in linux and feel that I should keep my headaches to a bare minimum :)

---

### Post by bschmiduk on 2006-07-17
I'm just a noob as well, but I think you want the i686 kernel.

I had a similar problem with my hyperthreaded 3GHz P4, and Ubuntu recognized the "second" core when I installed the 686 kernel.

---

