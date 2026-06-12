---
title: "processor problems"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by uk_sphinx on 2006-10-02
ok this isnt a problem but i would like an explanation to something.

alot of the threads i have read in the begginer section go on about is this amd or that amd compatible with ubuntu.
what has the processor got to do with a piece of software??
i thought a processer was full of swithches.

i never seem to see people say is it compatible with pentium though.
are amd processors totaly different to pentium processors or something???

this might seem like a stupid question but its just that i have never had amd coz i thought pentium were better.
if amd are better could someone let me know coz then i could get one.

---

### Post by paulyche on 2006-10-02
> **uk_sphinx said:**
> ok this isnt a problem but i would like an explanation to something.

alot of the threads i have read in the begginer section go on about is this amd or that amd compatible with ubuntu.
what has the processor got to do with a piece of software??
i thought a processer was full of swithches.

i never seem to see people say is it compatible with pentium though.
are amd processors totaly different to pentium processors or something???

this might seem like a stupid question but its just that i have never had amd coz i thought pentium were better.
if amd are better could someone let me know coz then i could get one.

People are probably talking about amd64 processors which are 64bit processors. Most intel and amd processors are 32bit and Ubuntu is equally compatible with both.

even 64 bit processors can work in a 32 bit mode and remain compatible with existing software. They just won't be able to use any 64bit optimisations.

It is possible to run specially optimised software for either amd or intel 32bit processors (see swiftfox for example), but most applications (including the standard ubuntu distribution) are just compiled to work on all 32bit processors

---

### Post by uk_sphinx on 2006-10-02
so ubuntu has to be compatible with the processor???
i dont understand why though
i thought the processors just knew on and off.coz there switches.
on and off in code is binary code right???
so do the amd64 do more than on and off???
iv probably just got a bad idea of how it all works in my head.

---

### Post by Marsolin on 2006-10-02
It does have to be compatible with the processor, but only from a broad standpoint. Essentially any Intel or AMD processor in the last ten years (since the Pentium II and K6) can run the i386 version of Ubuntu.

Ubuntu supports three architectures: i386, amd64, and powerpc. The first two apply to Intel and AMD processors. i386 is 32-bit and will run on any of those processors that I mentioned above. amd64 is 64-bit and will run on any AMD Athlon 64 or Opteron processor, any Intel Xeon processor since 2004, any Core 2 processor, and most Pentium 4 processors since 2004.

It's only if you are running the 64-bit version of Ubuntu that you need to check your processor for compatibility.

---

### Post by paulyche on 2006-10-02
If you had an old Mac for instance you'd need to use a version of ubuntu that's compatible with it, but on a PC ubuntu is compatible with anything that windows is (whether it's AMD or Intel). 

So yes, Ubuntu does need to be compatible with the processor, but it's not a big deal because it is made to be compatible with pretty much all the ones you're likely to come across.

As to why processors are different to each other. I admit I don't really know much about the differing architectures.

I asked a question about it myself a few months back..
[http://www.ubuntuforums.org/showthread.php?t=231597](http://www.ubuntuforums.org/showthread.php?t=231597)

However, the design of a processor is certainly more complicated than simply switches. There are such things as the amount of cache available and how big a chunk of data can be processed at any one time. So much that a piece of software compiled (where the actual human-readable programming language code is converted into something the computer can understand) for one processor probably won't work for another.

Like I said, I'm not really a authority on these matters.

You could try rooting around in wikipedia
[http://en.wikipedia.org/wiki/Microprocessor](http://en.wikipedia.org/wiki/Microprocessor)

---

### Post by uk_sphinx on 2006-10-02
ok

iv never really looked at progs for compatibility with processors.
i have pentium 4 3ghz
i guess i was lucky when choosing which ubuntu to download as i did see the i386 next to one version but didnt know what it meant.

---

### Post by paulyche on 2006-10-02
You probably noticed this bit:

> PC (Intel x86) desktop CD
    For almost all PCs. This includes most machines with Intel/AMD/etc type processors and almost all computers that run Microsoft Windows. Choose this if you are at all unsure.


Good luck with Ubuntu.

---

### Post by Marsolin on 2006-10-02
> **uk_sphinx said:**
> ok

iv never really looked at progs for compatibility with processors.
i have pentium 4 3ghz
i guess i was lucky when choosing which ubuntu to download as i did see the i386 next to one version but didnt know what it meant.

With that processor you can use either the i386 or amd64 versions.

---

### Post by uk_sphinx on 2006-10-02
is that because my processor is 64 bit and 32 bit 

excuse me if thats a dumb question it sounds dumb in my head

---

### Post by bulldog on 2006-10-02
> **uk_sphinx said:**
> is that because my processor is 64 bit and 32 bit 

excuse me if thats a dumb question it sounds dumb in my head

A 32 bit processor is not campatible with 64 bit.
A 64 bit processor is backwords compatible with 32 bit applications.

---

### Post by uk_sphinx on 2006-10-02
:oops: lol :oops:

i really shouldnt have asked that

---

### Post by bulldog on 2006-10-02
> **uk_sphinx said:**
> :oops: lol :oops:

i really shouldnt have asked that

Yep,you shouldn't :D :D 

But now you know.

---

### Post by Cruz on 2006-10-02
I don't see a reason why be ashamed for such a question. Those who ask learn and those who don't stay fools.

Well a CPU is actually more than just switches. A really interesting thing about them is the so called instruction set, which is pretty much like a miniature programing language that the CPU speaks. When a program is compiled lets say from C++ to machine code the C++ program is translated to instructions that the CPU can understand. Now the i386 is a common instruction base which all CPUs understand that belong to the family. However, some CPUs understand additional special instructions which others don't. You can compile software for such a special CPU so that it uses it's sepcial instructions and thus makes a program run more efficiently on this specific CPU, but doesn't run on others. That's where the issue "processor compatibility" kicks in. You can specificly compile ubuntu for let's say an AMD64 processor and then it will run really fast on AMD64 but it will run ONLY on AMD64. I hope that helps.

---

### Post by uk_sphinx on 2006-10-02
its not my fault[-( 
im blaming marsoline
damn u for making me ask that

:wink: as long as i push the blame to someone else i feel less stupid:-D

---

### Post by uk_sphinx on 2006-10-02
>  I don't see a reason why be ashamed for such a question. Those who ask learn and those who don't stay fools. 

very true

---

### Post by Marsolin on 2006-10-02
> **uk_sphinx said:**
> is that because my processor is 64 bit and 32 bit 

excuse me if thats a dumb question it sounds dumb in my head

Yep. That's why.

---

