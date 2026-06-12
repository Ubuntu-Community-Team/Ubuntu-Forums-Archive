---
title: "How can I delete the hidden recovery partition on my laptop?"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by fflarex on 2007-06-27
Gparted can't even see it, and I've run searches all over google and these forums without any answers. My 100GB hard drive is reduced to a mere 80GB after a fresh Ubuntu install, and I think a large portion of that is the hidden partition. Gparted simply says my hard drive has maximum capacity of 93.16GB.

So how do I get rid of it?

---

### Post by Circus-Killer on 2007-06-27
thats correct. if you bought a 100GB harddrive, its only gonna have 92GB.

tthis is because of the whole 1MB being 1024KB (and not 1000KB). that whole thing filters through to GB, and its become standard to make harddrives that way. it will always be smaller than what it sais.

---

### Post by Inxsible on 2007-06-27
1GB = 1024 MB and not 1000 MB. Maybe thats why you see your total hard drive size to be 93.xx instead of 100
 
My "160GB" hard drive only has a total available space of 149.8 GB. The vendors use the bigger numbers but naturally.
 
 
EDIT : Too late :rolleyes:

---

### Post by Circus-Killer on 2007-06-27
oh, and about that recovery partition, sounds like you've already successfully gotten rid of it (its not hidden). if you can use 93GB, then thats perfectly normal. thats the amount you ever gonna get.

---

### Post by Seisen on 2007-06-27
It's bascially there in case your hard drive needs to swap bad sectors, etc...

---

### Post by stchman on 2007-06-27
> **fflarex said:**
> Gparted can't even see it, and I've run searches all over google and these forums without any answers. My 100GB hard drive is reduced to a mere 80GB after a fresh Ubuntu install, and I think a large portion of that is the hidden partition. Gparted simply says my hard drive has maximum capacity of 93.16GB.

So how do I get rid of it?

Yes a 100GB hdd is actually 93.13GB as there are 1024MB in 1GB

So on a fresh install on a clean drive you go from 93GB to 80GB?  That is not possible.  Ubuntu takes about 3GB.  Do you have anything else installed other than Ubuntu.

---

### Post by fflarex on 2007-06-27
Okay, I guess everything is alright then. Gparted shows a 3.83GB extended partition & 3.83GB swap. I assume those double up for about 7GB plus the 3GB that Ubuntu uses, which *would* actually come to about 80GB.

---

### Post by joe.turion64x2 on 2007-06-27
If the partition is not visible in Gparted the it does not exist.

An easy conversion method from the GB advertised to the actual GiB (note the i between, it is a naming convention to avoid confusion, widely used in Linux) is to do the following. If your hard drive has **x** advertised GB then you have to compute:
**x**(10^9)/(2^30),
the result is your actual capacity (in GiB):
```

octave:1> **100***10^9/2^30
ans =  **93.132**
octave:2> 

```

[http://es.wikipedia.org/wiki/Gigabyte](http://es.wikipedia.org/wiki/Gigabyte)

---

