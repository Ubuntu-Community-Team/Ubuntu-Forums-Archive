---
title: "Apple vs Linux"
date: 2011-01-18
forum: Apple Hardware Users
---

### Post by kakashi_12 on 2011-01-18
Someone once told me that MAC is a distro of Linux or Unix.
 
If that is the case, how the heck did they get away with being able to charge for their OS and software? Isn't that against GPL?

---

### Post by VeeDubb on 2011-01-18
Mac OSX is based on Unix.

Unix and Linux are not the same thing.  They function in a similar manner, but that's it.  Linux was designed as a thesis project by a college student to show proof of concept that someone could create a unix-like system from scratch, and evolved from there.


Unix is not open source or subject to the GPL except where GPL code has gone back into the Unix kernel.

---

### Post by Hatsune Miku on 2011-01-18
> **kakashi_12 said:**
> Someone once told me that MAC is a distro of Linux or Unix.
 
If that is the case, how the heck did they get away with being able to charge for their OS and software? Isn't that against GPL?

Mac OS X is made from what is known as MACH more info is here: [MACH Kernel]("http://en.wikipedia.org/wiki/Mach_(kernel)")

Also Mac OS X is made from a system called NeXT Step. Which was made by NeXT in the 90s (steve jobs owned this company)

Linux was a project for a Computer science student (Linux Torvalds) to show anyone can make a UNIX kernel. He met Richard stallman working on the GNU OS project who made apps/tools he just needed a kernel. So the 2 fused them together to make of what is known as GNU/Linux

Mac OS X is considered a "Full UNIX" Meaning itself is a UNIX System. While Linux is what is known as "UNIX-like" Meaning it is like a UNIX, but missing some things that make it a "Full UNIX" System aka UNIX. Its Kinda confusing, but in the end Mac OS X and Linux share a lot in common for example Bash, Shell, Cron, UNIX system permissions, IPC system, and they also follow the UNIX philosophy of "Everything on a computer is just a file."

---

### Post by hawkmage on 2011-01-18
OS X uses a hybrid kernel (Darwin) based on the Mach and BSD kernels.  Darwin is licensed under the Apple Public Source License v2.  Like RedHat does with Linux Apple takes Darwin and layers on its proprietary additions and tools.

---

### Post by slooksterpsv on 2011-01-18
Some of the components in Apple's OS I believe are governed by the GPLv2. You can even go and download the source off of Apple's website. But some of the stuff is proprietary which they can charge for.

I get confused on it as well, but to each their own. (By the way, personal comment, I'm not sure what really differs between Unix and Linux, the functionality stays the same, the way they work stays pretty much the same, so what's different exactly?

---

### Post by VeeDubb on 2011-01-19
> **slooksterpsv said:**
> Some of the components in Apple's OS I believe are governed by the GPLv2. You can even go and download the source off of Apple's website. But some of the stuff is proprietary which they can charge for.

I get confused on it as well, but to each their own. (By the way, personal comment, I'm not sure what really differs between Unix and Linux, the functionality stays the same, the way they work stays pretty much the same, so what's different exactly?

Really good implied questions.

The reason that some is open and some is proprietary is that even within a single binary, there could be thousands or even MILLIONS of lines of code.  Some sections of those lines of code came from projects that were GPLed because it was easier to borrow existing code than to reinvent the wheel.  On the other hand, many other section were written from the ground up.  If you 'borrow' GPL code you have to keep it free and open, and share any developments that stem from it.  However, that doesn't mean you have to share the parts that are original work.


As for the difference between linux and unix, it's like the difference between a Toyota Corolla and a Ford Escort (do they make those any more?)

Anyway, they're both semi-compact, 4-door sedans with 4-cylinder engines, and they are operated in pretty much the exact same way.  You could even make the argument that one was developed to copy the other.  However, they developed 'mostly' independently of each other. 

The other thing to remember is that in the truest sense of the terms, Unix and Linux don't actually refer to operating systems.  In the purest sense, Ubuntu is not linux.  It's Ubuntu; which is a fully formed operating system based on linux.  Linux really only refers to the kernel.

The same is true of Unix.

Because Linux was originally built to function in the same way as Unix, the early shells for it were designed to use the same commands found in unix shells.  As both developed, some parts of the linux kernel were incorporated into some Unix kernels, which in turn, resulted in the code being shared back with the Linux kernel because it's required under the GPL.  (confused yet?)

The end result is that many unix kernels out there have a lot of GPLed code just like the Unix/BSD kernel used in OSX, and the linux kernel has a lot of code that was contributed from other projects.  While that results in a deep degree of similarity and interoperability, they are still separate project with different ideals behind them.

At the end of the day, there are still a million slight technical differences between the Unix and Linux kernels that has little if any effect on the end user, but some big idealogical differences and one technical difference that is pretty huge.

On the idealogical side, linux is open.  Everyone can contribute, even if it's just by having conversations on a forum that help explain things to people or filing bug reports.  Unix kernels are generally controlled by a single company and are completely closed except the parts that they are forced to keep open because of borrowed GPL code.

The big technological difference is caused by the openness.  Because linux is so open, and so many people contribute it has MUCH broader compatibility and arguably, better security as well.

---

### Post by Hatsune Miku on 2011-01-19
> **hawkmage said:**
> OS X uses a hybrid kernel (Darwin) based on the Mach and BSD kernels.  Darwin is licensed under the Apple Public Source License v2.  Like RedHat does with Linux Apple takes Darwin and layers on its proprietary additions and tools.

Actually OS X gets its BSD from the MACH kernel itself. MACH was made to replace a traditional UNIX kernel, they used BSD tools/components to make MACH.

---

### Post by Hatsune Miku on 2011-01-19
Dear GOD System glitch, Please ignore!

---

### Post by Hatsune Miku on 2011-01-19
Dear GOD System glitch, Please ignore!

---

### Post by hawkmage on 2011-01-19
> **Hatsune Miku said:**
> Actually OS X gets its BSD from the MACH kernel itself. MACH was made to replace a traditional UNIX kernel, they used BSD tools/components to make MACH.
Yes Mach started with BSD 4.3 but as Mach developed and evolved many of  the BSD constructs were replaced.  You may want to look at a branch of  BSD but not a decedent.  Later versions of BSD even borrowed its Virtual  memory manager from Mach.  

Take a look at "Mcx OS X Internals" by Amit Singh.  The kernel of OS X is xnu and is based on Mach 3 and FreeBSD 5 but is neither in its entirety.  Xnu uses Mach for low level stuff and adds in portions of BSD for the higher level kernel services.

It uses the Mach for the services layer like hardware abstraction,  processor managment, multitasking, Virtual Memory management, low level IPC constructs, and console  I/O.  The BSD layer implements the POSIX APIs, Async I/O APIs, IP Stack/BSD Sockets, Virtual File System Layer,  process management, and process synchronization primitives.

For example an OS X process is a BSD object but its threads are Mach objects.

---

### Post by Hatsune Miku on 2011-01-20
> **hawkmage said:**
> Yes Mach started with BSD 4.3 but as Mach developed and evolved many of  the BSD constructs were replaced.  You may want to look at a branch of  BSD but not a decedent.  Later versions of BSD even borrowed its Virtual  memory manager from Mach.  

Take a look at "Mcx OS X Internals" by Amit Singh.  The kernel of OS X is xnu and is based on Mach 3 and FreeBSD 5 but is neither in its entirety.  Xnu uses Mach for low level stuff and adds in portions of BSD for the higher level kernel services.

It uses the Mach for the services layer like hardware abstraction,  processor managment, multitasking, Virtual Memory management, low level IPC constructs, and console  I/O.  The BSD layer implements the POSIX APIs, Async I/O APIs, IP Stack/BSD Sockets, Virtual File System Layer,  process management, and process synchronization primitives.

For example an OS X process is a BSD object but its threads are Mach objects.

Yes, That just shows Mac OS X is not a BSD. But it still got most of its kernel code from MACH, It has BSD kernel code but only tiny bits. Anyway my point exactly is Mac OS X kernel is mostly MACH.

---

### Post by kakashi_12 on 2011-01-22
> **Hatsune Miku said:**
> Mac OS X is made from what is known as MACH more info is here: [MACH Kernel]("http://en.wikipedia.org/wiki/Mach_%28kernel%29")

Linux was a project for a Computer science student (Linux Torvalds)

Don't you mean Linus?

---

### Post by kakashi_12 on 2011-01-22
This is pretty sick...

[http://en.wikipedia.org/wiki/File:Unix_history-simple.en.svg](http://en.wikipedia.org/wiki/File:Unix_history-simple.en.svg)

---

### Post by smarmytime on 2011-01-23
There's a podcast called The Linux Action Show, and just about two weeks ago, they had [an episode]("http://www.jupiterbroadcasting.com/?p=4478") wherein a freeBSD guy on in place of one of the regular hosts, and they spent a few minutes on what Apple took from FreeBSD, and how Apple contributed back to FreeBSD. You would have to listen to about 3/4 of the podcast to hear it, and they only spend five or so minutes on the subject, but it's pretty good show, and just the segment about Apple and FreeBSD is worth the listen (or watch - it's a video podcast).

edit: I went back and listened to it, and the Apple stuff starts earlier than I thought, at the 13:50 mark.

---

### Post by BlastXng on 2011-01-23
As much as I would really like to use Linux on my G4 PPC Mac, I find it extremely frustrating that getting it to run isn't as easy as one would like it to be, especially on the PPC architecture unless you use Yellow Dogs Distro, which is very old.. 

At this point I am pretty close to throwing away the 16 hours or so I have spent to get my Mac G4 Cube up and running to go back to OSX 10.5 or move to FreeBSD.

---

### Post by linuxopjemac on 2011-01-24
Did you ever consider MintPPC ?

---

### Post by santosh83 on 2011-01-24
> **Hatsune Miku said:**
> Mac OS X is made from what is known as MACH more info is here: [MACH Kernel]("http://en.wikipedia.org/wiki/Mach_%28kernel%29")

Also Mac OS X is made from a system called NeXT Step. Which was made by NeXT in the 90s (steve jobs owned this company)

Linux was a project for a Computer science student (Linux Torvalds) to show anyone can make a UNIX kernel. He met Richard stallman working on the GNU OS project who made apps/tools he just needed a kernel. So the 2 fused them together to make of what is known as GNU/Linux

Mac OS X is considered a "Full UNIX" Meaning itself is a UNIX System. While Linux is what is known as "UNIX-like" Meaning it is like a UNIX, but missing some things that make it a "Full UNIX" System aka UNIX. Its Kinda confusing, but in the end Mac OS X and Linux share a lot in common for example Bash, Shell, Cron, UNIX system permissions, IPC system, and they also follow the UNIX philosophy of "Everything on a computer is just a file."

I may be wrong but I don't think Linus Torvalds & Richard Stallman actively collaborated or met with each other. Linus had heard of the GNU project previously, and he just decided to port their tools to his new kernel, rather than recreating them. It thus evolved into a GNU/Linux system.

Also I think to be certified as a "UNIX" a system needs to fully comply with the latest Single Unix Specification, apply to the OpenGroup for certification, and pass their tests, and not the least, pay a sizable sum. :)

---

### Post by conundrumx on 2011-01-24
> **santosh83 said:**
> I may be wrong but I don't think Linus Torvalds & Richard Stallman actively collaborated or met with each other. Linus had heard of the GNU project previously, and he just decided to port their tools to his new kernel, rather than recreating them. It thus evolved into a GNU/Linux system. 

I doubt either of the two big names had anything to do with the initial mingling of Linux and GNU.  GNU had tools but no kernel, Linux had a kernel but no tools.  If I recall correctly Linux was originally booted from MINIX.

> Also I think to be certified as a "UNIX" a system needs to fully comply with the latest Single Unix Specification, apply to the OpenGroup for certification, and pass their tests, and not the least, pay a sizable sum. :)

I somehow doubt the fee is that sizable - I'm sure Apple hasn't sold a single additional unit of OSX as a result of being a certified UNIX.  I'm sure they knew that going in, so I can't see why they'd pay a ton of money for it.

---

### Post by BlastXng on 2011-01-24
> **linuxopjemac said:**
> Did you ever consider MintPPC ?

Yes I have..

But I wonder if I will run into the same issues I am encountering now with my display, no sound and certain programs like the User and Group administration not working..

---

### Post by bilallucky on 2011-01-25
Unix and Linux are not the same thing. They function in a similar manner thats it. Linux was designed as a thesis project by a college student to show proof of concept that someone could create a unix-like system from scratch.

---

### Post by santosh83 on 2011-01-25
> **bilallucky said:**
> Unix and Linux are not the same thing. They function in a similar manner thats it. Linux was designed as a thesis project by a college student to show proof of concept that someone could create a unix-like system from scratch.

Was that the main reason? I remember reading somewhere that he was dissatisfied with MINIX's license at that time, and so set out to create a free Unix/MINIX clone.

---

### Post by gringo guy on 2011-01-25
> **kakashi_12 said:**
> This is pretty sick...
[http://en.wikipedia.org/wiki/File:Unix_history-simple.en.svg](http://en.wikipedia.org/wiki/File:Unix_history-simple.en.svg)

This one's my fave: [http://www.levenez.com/unix/](http://www.levenez.com/unix/) . . . if you mouse over the white band, right smack in the middle you can find mucho merges to and from OS X. Or, if you grab the PDF history file, Mac OS X enters stage left on page 11 and, as *Hatsune Miku* mentioned, forks from Mach 3 way back on page 8, and from Rhapsody (NeXTSTEP) on page 10, with merges from FreeBSD starting on page 11 (also where Rhapsody becomes OS X Server and forks to form Darwin), and on and on. What fun.

[And this doesn't even begin to diagram [the major linux distros]("http://en.wikipedia.org/wiki/List_of_Linux_distributions").]

---

### Post by Leovi on 2011-01-27
> **kakashi_12 said:**
> This is pretty sick...

[http://en.wikipedia.org/wiki/File:Unix_history-simple.en.svg](http://en.wikipedia.org/wiki/File:Unix_history-simple.en.svg)

:lolflag: I stand with you.

---

