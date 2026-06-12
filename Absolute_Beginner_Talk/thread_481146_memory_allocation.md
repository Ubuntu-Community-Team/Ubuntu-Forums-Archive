---
title: "memory allocation"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by fruzsi on 2007-06-22
Hi there,

I'm a new Ubuntu-user and have only a light knowledge about Linux in general. I'd like to know that how many gigs can be allocated or addressed by an application under Ubuntu? Ie I'm using Matlab for data processing and a reason to skip XP would be that there only 2 GB of memory could have been allocated.
thanks!

---

### Post by Sunforge on 2007-06-22
There are a lot of articles out there that look at the differences between Windoze and Linux memory management. 

How much memory can be addressed is the same across the board: a vanilla 32 bit OS only gives access to 4 Gb of RAM. If you've got a 64 bit OS version the sky's the limit although finding appropriate software and drivers can be a pain. Some 32 bit OS's can address more than 4 Gb of RAM using various fancy tricks that I don't pretend to understand.
[FONT=Times New Roman]
[LEFT]In terms of memory split for a 32 bit system quoting the first link below:[/LEFT]
[INDENT][LEFT]"in Linux and BSD, usually 3GB is kept for the process and 1 GB given to the kernel, while in Windows, 2GB are kept for each."[/LEFT]
[/INDENT][LEFT]Taking the author's word for it, you've got an extra gig to use but still have the 4 Gb upper limit, unless you're using a 64 bit version of the Ubuntu distro.

It also appears that Linux will, over time, gradually cache frequently used stuff into RAM to speed up apparent use, so memory use will grow over time. Judging by people's opinions this may be "good caching" or "bad programmes" memory leaking, so your mileage may vary.

Anyway on to the links:

The article which I quoted from:
[http://www.weblearn.hs-bremen.de/risse/RST/docs/Memory/comparison.pdf](http://www.weblearn.hs-bremen.de/risse/RST/docs/Memory/comparison.pdf)

And two more just for fun (well if you like reading articles about memory use)

The IBM article refers directly to Ubuntu Linux, which is a surprise:
[http://www.ibm.com/developerworks/library/l-linux-memory.html](http://www.ibm.com/developerworks/library/l-linux-memory.html)

This blog articles refers to chaching and has some comments on memory leaks:
[http://ubuntu.wordpress.com/2005/10/07/memory-swap-management/](http://ubuntu.wordpress.com/2005/10/07/memory-swap-management/)

I should point out that I'm a pretty vanilla Ubuntu user and so took the above articles at face value. 

Anway hope that this provides you with a starting point at least.[/LEFT]

[/FONT]

---

