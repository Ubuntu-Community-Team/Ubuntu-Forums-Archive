---
title: "Just Installed k7 kernel.  What are the advantages?"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-07-12
I had the 386 kernel, but since I have an AMD Athlon XP processor, I thought i might try the k7 kernel.  Am i supposed to notice any differences?  does it make it faster or something?  i haven't really noticed anything yet.

---

### Post by tribaal on 2006-07-12
Well yes, in theory the system should be faster.

Actually the different kernels (like the K7, i686,...) are more hardware specific, so they take better advantage of the processor's architecture, but cannot be used with another processor.

If you're a real performance freak I recommend you recompile your kernel yourself to fine tune it to your system (motherboard chipset etc), and then compile from source most of your packages (to optimise them to your system)... This is of course really time and energy demanding :( Gentoo linux does everything like this: they distribute source packages and the user compiles them once they are downloaded... Takes longer, but apps are faster (in theory).

Ubuntu chose to distribute 386 packages, so that they will work with as many architectures as possible, at the cost of a little speed.

With a modern system, the speed difference is pretty slim for our human perceptions :)

Hope this answers your quesiton :)

- trib'

---

### Post by user1397 on 2006-07-12
> **tribaal said:**
> Well yes, in theory the system should be faster.

Actually the different kernels (like the K7, i686,...) are more hardware specific, so they take better advantage of the processor's architecture, but cannot be used with another processor.

If you're a real performance freak I recommend you recompile your kernel yourself to fine tune it to your system (motherboard chipset etc), and then compile from source most of your packages (to optimise them to your system)... This is of course really time and energy demanding :( Gentoo linux does everything like this: they distribute source packages and the user compiles them once they are downloaded... Takes longer, but apps are faster (in theory).

Ubuntu chose to distribute 386 packages, so that they will work with as many architectures as possible, at the cost of a little speed.

With a modern system, the speed difference is pretty slim for our human perceptions :)

Hope this answers your quesiton :)

- trib'yep, you've answered it, thanks

---

