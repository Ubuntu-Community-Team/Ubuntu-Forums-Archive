---
title: "Which kernel is best for Intel Pentium 4"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by DapperDrake2007 on 2007-02-12
Hi,

My computer has an Intel Pentium 4 processor.

Which linux kernel is best for me, -386 or -686?
What's the difference between them?

Thanks in advance for the reply.

---

### Post by docshawnc on 2007-02-12
the 686 supports dual processors - if you have a P4 with hyperthreading, then that's the one to use.  If it's not a hyper-threaded P4, the 386 is the one to use

---

### Post by an.echte.trilingue on 2007-02-12
The difference is the architecture that they were compiled against.  The 386 kernel is for 386s and newer, the 686 is for 686s (aka, pentiumII) and newer.

In theory, the 686 should be faster for you.  I can't tell the difference, personally.

Take care
-mat

---

### Post by an.echte.trilingue on 2007-02-12
> **docshawnc said:**
> the 686 supports dual processors - if you have a P4 with hyperthreading, then that's the one to use.  If it's not a hyper-threaded P4, the 386 is the one to use
Are you sure about that?  That is not at all [my understanding]("http://ubuntuforums.org/showthread.php?t=85917")

Take care,
-mat

---

### Post by DapperDrake2007 on 2007-02-12
My P4 is not a hyper-threaded one. So, should I stick with the 386?

---

### Post by wh0rd on 2007-02-12
Eeven if you have HT, stick with the Generic Ubuntu supplies.

---

### Post by mendingo84 on 2007-02-12
i also have Intel P IV 3.0 Ghz, no HT and i'm running the 386 version...everything is smooth, enjoy!

---

### Post by docshawnc on 2007-02-12
> **an.echte.trilingue said:**
> Are you sure about that?  That is not at all [my understanding]("http://ubuntuforums.org/showthread.php?t=85917")

Take care,
-mat

Hi Mat -
     Hmmm, I was not aware of that - (just repeating what I've been told).  I've never tried a 868 kernel with a non-hyperthreaded or non-dual core machine so I don't know what would happen.  The 686 does make the latter machine work quite a bit better though - thanks for the info

---

### Post by an.echte.trilingue on 2007-02-12
> **docshawnc said:**
> Hi Mat -
     Hmmm, I was not aware of that - (just repeating what I've been told).  I've never tried a 868 kernel with a non-hyperthreaded or non-dual core machine so I don't know what would happen.  The 686 does make the latter machine work quite a bit better though - thanks for the info
I don't really know either, I really was asking.  I understood that you need an SMP kernel for dual core processors and 686 was for, well, 686's, although Ubuntu and Debian have been changing the nomenclature for kernels recently and I haven't installed the latest and greatest so I am not sure...

Take care
-mat

---

### Post by DapperDrake2007 on 2007-02-12
One more question. If I install a secod 686 kernel and I leave my current 386, will I be able to use both (i.e. select the kernel when I boot)?

BTW, the 386 kernel runs smoothly now, I was just wondering if the 686 is not better for anything that is not a 286.

---

### Post by Moffett on 2007-02-12
Hi i just installed 6.10 on my computer a few hours ago and am trying to get control of it. Looking over the forums for ideas to help get this running best on my computer i come across this thread. I have a Pentium 4 with HT but i have no idea what kernel i am using nor do i know how to find out. Can someone tell me how to check and install the proper one for best results. I honestly have no idea what im doing and need a bit of help

---

### Post by r4ik on 2007-02-12
Type uname -a in a terminal it will tell you wat you have got.

---

### Post by an.echte.trilingue on 2007-02-12
> **DapperDrake2007 said:**
> One more question. If I install a secod 686 kernel and I leave my current 386, will I be able to use both (i.e. select the kernel when I boot)?

BTW, the 386 kernel runs smoothly now, I was just wondering if the 686 is not better for anything that is not a 286.

Yes.  To select the kernel, when your computer is first booting, hit escape to get into the grub menu, then you can select with the arrow keys.

Take care
-mat

---

### Post by DapperDrake2007 on 2007-02-12
Great. Thanks a lot for your help.

---

### Post by NT4usB on 2007-02-12
...been wondering about this myself.
In 6.06, I have installed the 686-smp kernel. Works fine.

When I look at the 686-smp on my 6.10 box it says it's been "obsoleted by the -generic and is retained only for upgrades..." or, some such?
So what's the real poop? 
Does the -generic support smp?

---

### Post by konst88 on 2007-02-12
The generic kernel checks your CPU, and uses the best kernel for it.
It supports all the kernel types.

---

