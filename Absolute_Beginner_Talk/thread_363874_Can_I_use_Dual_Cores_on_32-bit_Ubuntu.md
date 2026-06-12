---
title: "Can I use Dual Cores on 32-bit Ubuntu?"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by Troubled on 2007-02-17
After installing the standard (32-bit) release of Ubuntu on my computer and working with it for a while, I realized that it wasn't using both of the two CPUs that my dual-core system has. Can I make full use of a dual-core processor with a 32-bit operating system?

---

### Post by Crakie on 2007-02-17
32 or 64 bit has nothing to do with single or dual core. So yes, you can use 32 bit Ubuntu just fine for your system and use both. I do too :)

How do you know it's only using one?

---

### Post by Troubled on 2007-02-17
I did run this one command that I read about somewhere that checked CPU temperature and whatnot (but forgot what the command was), and it showed me only 1 CPU temperature reading. But really, I had this notion that 64-bit OS's were needed to use a dual-core processor. Pardon my computer idiocy. :(

Ooh, you're right, it seems that both CPUs are being used by default (or at least detected by the device manager). But, how could I confirm that they're both being used?

---

### Post by P235 on 2007-02-17
cat /proc/cpuinfo

Enter that command into your cli, you should be able to see processor: 0 and processor: 1.  If you see two processors then the two cores are at use.

---

### Post by Troubled on 2007-02-17
>cat /proc/cpuinfo
>
>Enter that command into your cli, you should be able to see processor: 0 and processor: 1.
>If you see two processors then the two cores are at use.

The command shows me two processors. :)

Thanks for all of the help!

---

### Post by Crakie on 2007-02-17
> **Troubled said:**
> Pardon my computer idiocy. :(

Don't be too hard on yourself :popcorn: 

Just to clarify a little, dual cores show themselves in software as two processors, but physically they are a single chip. Kind of a two-for-one deal. I am not an expert, but that would explain why you saw only one temperature: there is only one chip, which has a single temperature!

---

