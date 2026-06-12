---
title: "Max RAM for a 32-bit OS?"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by Yes on 2007-11-29
I've heard that the max is 4 GB for a 32-bit OS.  But then I've also heard that 32-bit Windows can only use 3.25 GB of RAM.  So how much can Ubuntu handle?

Thanks.

---

### Post by Dark_X on 2007-11-29
I heard it was 3.25.

---

### Post by skymera on 2007-11-29
4GB max, and 16GB for 64 bit.

but can also depend on OS

---

### Post by jerrylin on 2007-11-29
It is 4gb max (2^32), however some of that address space is reserved for special purposes, used to address your video card memory, and so on. After all this comes into play, your OS will give you something around ~3.25gb depending on your hardware.

This will be true regardless of OS (Windows or Ubuntu). It is a hardware limitation.

---

### Post by jerrylin on 2007-11-29
> **skymera said:**
> 4GB max, and 16GB for 64 bit.

but can also depend on OS

Actually, for a 64-bit machine (64-bit address) you can have 2 ^ 64 unique addressess. Since our computers are byte addressable, you can have 2^64 bytes which amounts to... 18446744073709551616 bytes (or 2 eb).

Here is a great explaination:  [http://www.codinghorror.com/blog/archives/000994.html](http://www.codinghorror.com/blog/archives/000994.html)

---

### Post by Yes on 2007-11-29
Ok, but I won't have any problems with 3 GB?

---

### Post by -grubby on 2007-11-29
> **Yes said:**
> Ok, but I won't have any problems with 3 GB?

you shouldn't ( have any problems )

---

### Post by jerrylin on 2007-11-29
It depends... if you have 2 GeForce 8800's in SLI, each with 768mb of ram, you will not be able to use a full 3gb either. I would estimate a normal system today with a 256mb video card would get about 3.3-3.4gb of ram they could use... Any more video ram I say just count down from there.

---

### Post by PmDematagoda on 2007-11-29
> **skymera said:**
> 4GB max, and 16GB for 64 bit.

but can also depend on OS

I have heard that the maximum for 64 bit Linux was actually 64 Gb of RAM.

---

