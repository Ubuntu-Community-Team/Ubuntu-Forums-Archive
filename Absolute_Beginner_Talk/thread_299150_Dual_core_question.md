---
title: "Dual core question"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by moilzpoil on 2006-11-13
When searching in "packages" for "linux-headers" there are 386 options

 and a 686 option.  Is this for dual core processors?  Thanks

---

### Post by b_martinez on 2006-11-13
Look for the kernel(s) and headers that have SMP support, since you are running dual processors. These will, in my opinion, give you the best performance. Since you already paid for them,use them.
Bill

---

### Post by Velotix on 2006-11-13
The only problems associated with dual-core CPUs are getting the BIOS to recognise them in the first place and a couple of minor issues related to (bizarrely) broken graphics card drivers.

In other words, if you have 32-bit Ubuntu, stick with i386 and you won't go wrong. As I understand it the Linux kernel used to have specific optimisations for certain versions of Intel-compatible 32/64-bit processors but is now making the kernel generic, so your question is probably moot at this point in time anyway.

If you're using 64-bit Ubuntu (and if you have a dual-core as I do that's perfectly reasonable) then look for i386-64 stuff. There's considerably less software available for that right now though which is why most people are sticking with the 32-bit version for the time being.

**EDIT:** [Deleted. See my next post.]

---

### Post by autocrosser on 2006-11-13
I'm running a Pent D 840 (dual 3.2) & running edgy--the kernel is 2.6.17-10-generic & both cpus work great (kernel is listed as SMP)--I also add the line "ht=on" in the kernel line in Grub---My kernel log indicates that Hyper-Threading has been enabled;)

All depends on what dual core unit you have----

---

### Post by moilzpoil on 2006-11-13
Sorry about the double post.  Thanks for the info. Just now loading

 Ubuntu on the 750mz Sony laptop to see if that changes how easy it is to

 configure compared to the dual core. Might explain a few results.

---

### Post by musicinmybrain on 2006-11-13
If using Dapper you want one with "smp" in the name, e.g. "686-smp." 686 means the kernel was compiled to be optimized for Pentium II or newer. "smp" means symmetric multiprocessing, or multiple cores.

If using Edgy, just get the "generic" kernel.

---

### Post by dbbolton on 2006-11-13
i think it's just 6th generation x86 architecture

---

### Post by Velotix on 2006-11-13
> (Quoted from deleted segment of my post:)
I think i686 stuff is optimised for Pentium 4 processors so it would be no use to you anyway. If Linux had stuck with the old specific kernel versions then the dual-core processors would be i786. ^^

Well, I was wrong. This is probably more information than you wanted, but it should make things clearer to you in future. ^^

Actually, doing a quick read-up on it suggests that i686 should actually refer to the Pentium II, if we stick to the age-old Intel naming convention.

"i386" refers to the fact that Linux was originally developed for the Intel 80386 (shortened to i386) processor, and until recently the technology at the core of Intel's processors has never deviated far from this 20-year-old blueprint, which is why i386 Linux is so well built now, and why x86-64 Linux is a considerably weaker implementation, as 64-bit processing throws everything on its head.

The name Pentium comes from the fact that Intel couldn't trademark "80586" and "pent" is Latin for "of order five" or something very similar to that (hence "pentagon", which has five sides).

If Intel had stuck with that old naming convention instead of being forced to invent a brand name, then we'd now have the following:

80586 - Pentium I
80686 - Pentium II
80786 - Pentium III
80886 - Pentium 4
80986 - Core (it was very short-lived - I hadn't heard of it until after Core 2 was released, in fact)
81086 - Core 2

I'm guessing then that "i686" refers to anything that was optimised to take advantage of the MMX technology introduced as a standard feature of the Pentium 2. In short, it really won't make any difference if you don't use it because I don't think MMX is used much anymore anyway.

BTW, if you were wondering about where the Pentium D fits in all this (and if you were then I'm most surprised :P), it doesn't. Pentium is now a brand-name used to refer only to lower-end processors - slightly more upmarket than the Celeron D, but still low end - probably to keep the masses happy. ^^

*whew*

---

### Post by PriceChild on 2006-11-13
*threads merged*

---

