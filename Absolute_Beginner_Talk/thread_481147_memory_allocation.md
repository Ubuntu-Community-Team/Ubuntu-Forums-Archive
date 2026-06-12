---
title: "memory allocation"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by fruzsi on 2007-06-22
how many gigs can be allocated or addressed?
I'm a new Ubuntu-user and have only a light knowledge about Linux in general. I'd like to know that how many gigs can be allocated or addressed by an application under Ubuntu? Ie I'm using Matlab for data processing and a reason to skip XP would be that there only 2 GB of memory could have been allocated.
thanks!

---

### Post by hyper_ch on 2007-06-22
It depends on your system... in some other thread people said that 32-bit system can only hold up to 3gb.

---

### Post by pmg on 2007-06-23
3Gig per process sounds right.  As I recall it's just a little under that.  Keep in mind that 32bits is 4Gig, and some of that is needed for device addresses, text, mapping into kernel and the like... 

But that's were 64bit comes in - in fact that's the whole point of it.

---

### Post by Warpnow on 2007-06-23
What kind of process can use more than 3 gigs of ram?

---

### Post by pmg on 2007-06-23
> **Warpnow said:**
> What kind of process can use more than 3 gigs of ram?
Big ones!  :-)     Sorry, I couldn't resist.

There must be enough demand for it to justify all the hardware manufacturers to be investing so much in 64bit.  I know various types of simulations can be very large.  Some CAD apps need big process address spaces.  Some large databases need that much RAM for performance.  Some scientific/enginerring apps can get very big.

---

