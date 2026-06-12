---
title: "What is compiling a kernel?"
date: 2005-10-05
forum: Absolute Beginner Talk
---

### Post by floyd27 on 2005-10-05
I see these how-tos all over the place..
What is it..?

Not how to do it but what r they doing ?

---

### Post by Ampersand on 2005-10-05
It's similar to compiling any other software. It involves changing what is included in the kernel to either add support for hardware or optimising it for a certain task. (The act of compiling converts a program from its source code into binary.)

---

### Post by cwaldbieser on 2005-10-05
[QUOTE=floyd27]I see these how-tos all over the place..
What is it..?
Not how to do it but what r they doing ?[/QUOTE]
The kernel is the software part of the computer that interacts with the hardware and basically schedules all the other programs to be run.  It is a very important piece of the computer, but one that you can't really see, like an music player or a video game.

Compiling a kernel means that you are building that program from the source instructions.  It allows you to tweak the configuration so that it has support for things you want, but doesn't have support for things you don't want.

---

### Post by az on 2005-10-05
[QUOTE=floyd27]I see these how-tos all over the place..
What is it..?
Not how to do it but what r they doing ?[/QUOTE]
Years ago, there was very little hardware detection and so forth.  The stuff worked, but you had to configure everything by hand.

You would install a linux distribution that would ship with a kernel that had a reasonable set of options (driver or modules) turned on.  This made the stock kernel bigger and slower.  It was really uncool to run a stock kernel for very long.  You basically installed your system and compiled your own kenrnel with all the drivers and options that was appropriate for your machine.

If you bought a new sound card, you had to recompile your kernel to get it to work.  

Several years ago, as linux use got more and more popular, and it was used less for specialised computer geeks, people started to write ways to autodetect hadware and a distribution would compile most of the available kernel drivers as modules which would be loaded on demand.  This solved the problem of slow bulky kernels and eliminated the need for most people to have to recompile their kernel.

Most of the time, if you need a driver that is not in the stock kernel, you can compile it alone, using the kernel headers.  (linux-headers-2.6.10-5-386, for example.  It must match your running kernel version)

Hope that helps.

---

### Post by floyd27 on 2005-10-05
well at least now i know whats going on a bit..
it helped alot actually.
I will find some more articles and read up on it some more.. It sounds like something id be interested in learning more about..
thanx

---

### Post by az on 2005-10-06
[QUOTE=floyd27]well at least now i know whats going on a bit..
it helped alot actually.
I will find some more articles and read up on it some more.. It sounds like something id be interested in learning more about..
thanx[/QUOTE]
Find an old computer and install Debian Woody (or Potato) on it.  That's a fun way to blow away a weekend or two...  Try an ancient version of slackware, too!  (Match it to the manufacture date of the motherboard)  (Extra points to install it on modern hardware!)

---

