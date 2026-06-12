---
title: "System Architectures"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Squizz on 2008-01-17
This question isn't Ubuntu specific - but I wonder if anyone could tell me anything about the available system architectures?

I realise we have i386, amd64 and powerpc architectures, but are there any other ones worth considering?

Thanks!

---

### Post by mr32123 on 2008-01-17
I'm not exactly sure what you're asking about, but basically there are three major "architecture" types.

i386 which is most common right now.  These are the single core intel processors.
x64 the dual core intel processors. Have taken over the market, and slowly rising to power.
and of course there's AMD.

Now I'm not sure what you're considering, but from my own personal experience my AMDs have had serious heat issues.  The single core Intels I bought I am very happy with (P4 2.6GHz and 3.00GHz)  Haven't tried the dual cores or the new AMDs but my friends have one of the dual cores and seems to be happy with it, however the stress he puts on his computer comes nowhere near mine.

---

### Post by Squizz on 2008-01-17
I was just curious as I've now installed 64 bit Gutsy on my own machines, i386 Edubuntu on a machine for my nephew and powerpc Xubuntu on an old G3 - so was wondering if there were any other architectures I didn't have a linux distro for should the need arise ;)

Modern Macs and PCs use the same architecture now though don't they?  None of this Mac OS only nonsense I assume?

---

### Post by PeterJS on 2008-01-17
The list of things debian runs on is fairly complete.
[http://www.debian.org/ports/#released](http://www.debian.org/ports/#released)

---

### Post by chach man on 2008-01-17
some servers have different architectures (i486, i586, I believe there is also an i686) if they say x86 then it will work on those architectures as well. Ubuntu wouldn't be my first choice for a server tho unless it's a small low traffic server.

---

### Post by PeterJS on 2008-01-17
> **chach man said:**
> some servers have different architectures (i486, i586, I believe there is also an i686) if they say x86 then it will work on those architectures as well. Ubuntu wouldn't be my first choice for a server tho unless it's a small low traffic server.

The x86 family is interesting. I've never actually seen anything built with i486, or i586 optimizations, and the only thing I've even seen built i686 are gentoo and libc. For the most part you can use x86 and i386 interchangeably because there are so few things built to use the i686 extensions.

---

### Post by Redache on 2008-01-17
I386, 1686, IA64, AMD64, Sun SPARC, Alpha, Power PC, ARM and so on.

ARM's are used mainly in Mobiles and small devices.
x86's are mainstream desktop.
IA64 is used in Servers/Super Computers and was done for the Intel Itanium.
AMD64 is the "mainstream" 64-Bit Architecture.
SPARC's are used for Servers made by Sun and are and interesting technology (Like the 128 Core Processor) and are good for Super computer/Server stuff. Would be overkill for a chunk of corporate users though.
Alpha is RISC based and was developed by DEC but is no longer made. There are some Supercomputers around the world that still use it.

There are many more if you go to the 80's and look at some of the more Custom architectures. But the ones up there are the common one's you'd find today.

---

### Post by SOULRiDER on 2008-01-17
> **PeterJS said:**
> The x86 family is interesting. I've never actually seen anything built with i486, or i586 optimizations, and the only thing I've even seen built i686 are gentoo and libc. For the most part you can use x86 and i386 interchangeably because there are so few things built to use the i686 extensions.

Packages in Arcglinux are built for 686

---

### Post by sumguy231 on 2008-01-17
> **mr32123 said:**
> I'm not exactly sure what you're asking about, but basically there are three major "architecture" types.

i386 which is most common right now.  These are the single core intel processors.
x64 the dual core intel processors. Have taken over the market, and slowly rising to power.
and of course there's AMD.

Now I'm not sure what you're considering, but from my own personal experience my AMDs have had serious heat issues.  The single core Intels I bought I am very happy with (P4 2.6GHz and 3.00GHz)  Haven't tried the dual cores or the new AMDs but my friends have one of the dual cores and seems to be happy with it, however the stress he puts on his computer comes nowhere near mine.
I hate to nitpick, but there are a couple factual errors here:

32-bit AMD processors aren't part of their own separate architecture, they're all i386 compatibles. What's more, not all dual-core Intel processors are 64-bit. 
Also let the record show I have multiple computers with AMD processors and the only computer I've ever had overheating problems on had a Pentium 4. I don't think AMD processors in general are any more or less likely to overheat.

---

### Post by mattismyname on 2008-01-17
Thank you sumguy231, I just about fell off my chair when I read 32bit == single core, 64bit == dual core.  The two are absolutely, 100% unrelated.

---

### Post by chach man on 2008-01-18
yes, absolutely I missed that when I read through the first time 64bit and 32bit refer to data path width (amount of data able to be put on the bus at a time). 

single and dual core refer to the processor exclusively.

its widely rumored that AMD's run hot but I've never heard people complain about them burning out so I'm kind of assuming it is just a rumor. I've also heard that dual cores don't run as hot (my AMD64 x2 is running at a normal temp)

---

