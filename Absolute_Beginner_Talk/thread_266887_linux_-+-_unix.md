---
title: "linux -+- unix"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by uk_sphinx on 2006-09-27
what is the differance between linux and unix?

---

### Post by comppsyco on 2006-09-27
I don't understand it all that well, but I believe that Unix was for a long time a commercial operating system used for distributed computing and scientific workstations, among other things, and in the early 90s Linus Torvaldis decided to make an open-source, free OS out of Unix. What I don't know is, did he start with a Unix kernel or did he code it from scratch? Now I'm curious.

---

### Post by uk_sphinx on 2006-09-27
thanks for replying im courious on that too
does anyone still use unix to this day or is it a bygone os?

---

### Post by comppsyco on 2006-09-27
I know that it's still used on older scientific workstations, but I think that that too is being supersceded by linux, and to some extent, OS X. The most Unix-like os being used by real people, I think, is FreeBSD. But again, I'm not entirely sure about any of this, so don't quote me.

---

### Post by b_martinez on 2006-09-27
From what I understand, Linus started coding the linux kernel after coming across minix, a minimalistic Unix offshoot. He also took the unusual step of opening it up (almost?) immediately to development. It is a Unix 'clone'. It operates in much the same way and can use some of the Unix software.
  As far as Unix, it is still a viable OS, used in large mainframes in business and educational institutions. Some government apps too.
  BSD's are all derived from 'Berkeley Software Development' (I think that is what BSD means.) In it's early days, Unix was developed much as Linux is today. Much development was done at Universities, Berkeley in the forefront. There came a time when Unix System Labs realized that Unix could be a money maker, and tried to put a stranglehold [read copyrights] on Unix. Long, involved lawsuit.
 For a synopsis of the timeline, visit 
[http://www.groklaw.net](http://www.groklaw.net)
and look on the left side for a book by Dr. Salus, or just click this link
[http://www.groklaw.net/staticpages/index.php?page=20051013231901859](http://www.groklaw.net/staticpages/index.php?page=20051013231901859)

Hope this sheds some light for you.
Bill

---

### Post by comppsyco on 2006-09-27
Thanks!

---

### Post by uk_sphinx on 2006-09-27
thanks

---

### Post by b_martinez on 2006-09-27
You're welcome. If you are curious about Unix, you can D/L install Open Solaris, It is a true Unix OS. OR you can d/l and burn to cd,
1) Freesbie (a live cd based on FreeBSD) 
2)Dragonfly, another BSD, but I'm not sure it is "Live"

I liked Freesbie, but I got curious about (X)(K)Ubuntu, and since I'm trying to convert (yes, I mean 'to turn around') some co-workers, I thought Ubuntu and derivatives would be good to learn, so I could help them. And I AM learning, slowly, oh so slowly.
lol
Bill

---

### Post by szf on 2006-09-27
There is a book titled *_Just For Fun_* that covers the life of Linus Torvalds at the genesis of the Linux kernel.

The book does not appear to be in the public-domain or GNU FDL... but [here's]("http://www.firstmonday.org/issues/issue3_3/torvalds/") an interview back when the book was "to be published."

---

### Post by b_martinez on 2006-09-27
Good read, thanks for posting it.
Bill

---

### Post by n0dl on 2006-09-27
Although GNU stands for Gnu is not unix, and even though linux is licensed under GPL, Linux is none the less a Unix operating system written for a PC. Unlike the other Unices, Linux was written specifically for the x86 architecture, unlike others such as the BSDs which are basically a Unix Operating System **ported** to the PC. Linux and Unix are one in the same to be quite honest. Linux is simply a flavor of unix just like BSD, HPUX, IRIX, and Solaris is. They all use the same tools, all are governed by a kernel and what not. Therefore the question should not be "what is the difference between Linux and Unix." But should be "What is the difference between Linux and UnixFlavor0" where UnixFlavor0 is another unix operating system. Some general difference (that I know of) are:
Base system: Linux is just the kernel. Everything else is an add on: GCC, ls, rm, cd etc. In the other Unices particularly BSD, the base system includes system tools such as ls and rm already built into them.
Parameters: Commands similar to linux sometimes have different options than in linux.
Ports: Basically ports to a system does not necessarily mean the "actual version." Take GCC for example. In linux GCC version 4.03 means GCC version 4.03. In other unices such as BSD GCC version 4.03 means a port of GCC based on GCC version 4.03. 
Binaries: Package managers (except for portage) usually distribute software through binaries. In most unices, while binaries are sometimes available, if you want a peice of software it usually means you have to port the software to your OS. Hence the Ports tree in FreeBSD. 
There are alot more difference but i cant recall all of them from memory. Hehe :D

---

