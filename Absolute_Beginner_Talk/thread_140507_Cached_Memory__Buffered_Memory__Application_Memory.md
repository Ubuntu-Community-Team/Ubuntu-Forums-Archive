---
title: "Cached Memory / Buffered Memory / Application Memory ?"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by derbaschti on 2006-03-06
This may be a stupid question, but can somebody explain to me, what Cached Memory / Buffered Memory / Application Memory actually mean? When I open Ksysguard, i get their usage shown in different colors. 
Also, they almost always sum up to just slightly less than my total RAM, regardless which and how many programs I am running... Is this normal?

---

### Post by ARhere on 2007-11-17
I know the meaning of these terms as it applies to electrical engineering, but it may not be entirely accurate for the Ubuntu OS.

1.  Because the Hard drive your PC uses is extremely slow, the PC will store commands/programs it uses a lot in a section of your available RAM to make things go a lot faster, this is called [cached memory.]("http://en.wikipedia.org/wiki/Cache")

2.  A [buffer]("http://en.wikipedia.org/wiki/Buffer_%28computer_science%29") is an memory space that two different components will use to transfer data easily to each other.  In a way, the memory on your PC can be used as a universal buss for two devices (*hardware or software*) that don't share a buss directly.

3.  Application memory is just that, memory set aside for applications that you are using.

The reason why I said it may not be correct for Ubuntu is because I do not know how Ubuntu (really the Linux Kernel) uses these memories.  I know it will really slow things down if you run out of buffer and application memory, but I am not sure if the Linux kernel will always use all available memory for caching.  It would make your PC a lot faster, but may give the impression that you are running out of memory.

A more experienced Linux geek needs to step in here.

-ARhere

---

