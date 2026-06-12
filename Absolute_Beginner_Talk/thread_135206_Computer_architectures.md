---
title: "Computer architectures"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by Klaidas on 2006-02-23
Hello :)

I have some question about computer architecture... (It's not for choosing the CD to download, I already have Ubuntu installed and succesfully using it :) ). It's just that I would like to know the diffrences between them.

Could someone guide me through this briefly?

Thanks, 
Klaidas

---

### Post by Solver on 2006-02-23
Labas dienas :).

So, as you know, the standard Ubuntu is for 32-bit PCs and there's also one for the 64-bit architecture. Basically, in a 32-bit PC, the processor (CPU) uses 32 bits to denote memory addresses, to store values in registers, and so on. 32 bits means 4 octets - that is, 4 groups of eight bits, or 4 bytes.

For example, the processor can reference memory locations such as 0000:0000 or 2ab3:fe07. Here each 2 digits are a byte, so 8 digits for 4 bytes. It means that overall, the processor can thus reference 2^32 locations in memory, which is 4 GB of memory. 64-bit processors can reference memory addresses with the length of 64 bits or 8 bytes, so that's up to 16 EB (exabytes) of memory. Quite a lot.

Without getting into details, many programs can also work considerably fster if they have access to 64-bit processors. This is for reasons related to memory mapping and other reasons. However, to get a real performance boost, programs/operating systems have to be written especially for 64-bit processors. They won't run on 32-bit processors then, but will perform better on 64-bit ones. Or, some programs can use 64-bit capabilities but are still compatible with 32-bit machines.

---

### Post by heimo on 2006-02-23
It's a bit broad subject... But I've found these articles very interesting and educating (see the older articles on the bottom of the page).
[http://arstechnica.com/articles/paedia/cpu.ars](http://arstechnica.com/articles/paedia/cpu.ars)

---

