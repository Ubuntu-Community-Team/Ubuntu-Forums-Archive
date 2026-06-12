---
title: "Should I change to x64?"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by falkTX on 2008-04-10
Hi everyone!

I have a question - Should I change my i386 laptop to x64?

I'm currently using Hardy (Beta), I have an AMD x64 turion (or something like that), 2Gb ram 120HDD.
I heard that x64 system makes the processor do things a lot faster, is it true?
And what about my hardware? (DVB-T ; IR ; Graphics card ; Bluetooth ; Joysticks ; etc..)
Will they work fine on my laptop?

If you already tried, please tell me how it was and why (please)
If you don't, don't bother

Thanks

---

### Post by zvacet on 2008-04-10
I´m not an expert,but I think you will feel the difference if you have >4GB of ram.In case thar you don´t plan to upgrade your hardware 32 bit should be fine.

---

### Post by smartboyathome on 2008-04-10
I think looking in the long term it would be better to switch to x64. I use it on my desktop, and it works great, especially with heavy processing like gaming and blender. Its more of a preference based on what you are doing though.

---

### Post by Therion on 2008-04-10
Until Hardy, I was running 32-bit versions of Linux.  Having run Hardy 64-bit for the last few weeks I can tell you it... is... awesome.

I can't compare 32-bit Hardy to 64-bit Hardy, but I can tell you that 64-bit Hard positively flies (no pun intended) on my AMD 4200+ X2 (2GB of system RAM).  For me there's no going back.  And I had none of the problems of previous 64-bit distros regarding Flash, etc.  Everything has been flawless for me with Hardy 64-bit.  And wow it's fast...  Just... Wow.

And no one is really going to be able to tell you with certainty that YOUR particular hardware is going to work with a particular distro or "bit" version.  You're simply going to have to download some LiveCD's and see what works for you.

---

### Post by guitarMan666 on 2008-04-10
I don't think you should switch unless you KNOW you have a 64 bit processor.  If you do, the performance increase is supposed to be OK at least, if not phenominal.

---

### Post by Inxsible on 2008-04-10
It doesn't matter what others are using their machines for. What does matter is what will YOU use your machine for.

If you are going to use your machine just to browse the web and a couple of chat softwares, there is hardly any point going thru the entire installation process.

But if you do plan to use cpu-intensive apps...like Blender (as mentioned earlier) or others..then going to a 64 bit might actually be helpful


Note that there are small issues when you want to install 32bit software on a 64 bit OS. Skype comes to mind -- since I just recently installed it. You would have to install 32 bit libraries in addition to the 64 bit ones your machine would have. When it comes to such, you should be willing to use the command prompt - as you most likely will have to change a few settings here and there

---

### Post by tribaal on 2008-04-10
Simply put:

- If "cat /proc/cpuinfo" shows "lm", you have a 64bits-able CPU.
- x64 is faster for floating point calculations (anything graphic for example).
- Whatever works on your 32 bits OS will work on x64, as long as it's in the repositories (yes, including flash and Java, they just work).

Fact: my x64 Installation is awesome :) - it flies, it just works, and it's future proof.

- Trib'

---

### Post by cotcot on 2008-04-10
I measured the performance increase on my box. I had up to max 30 %. So nice but not phenomenal. I tried with 3 GB ram but that did not increase the speed. It was not used for more than 1 GB. I run 32 and 64 in multiboot. I need the 32 bit for the printerdriver.

---

### Post by dwblas on 2008-04-10
With a 120 gig hard drive you should have plenty of room for an additional install.  I would suggest a separate partition and a separate install for the 64 bit version.  Most programs now work with a 64 bit processor, but if you have problems and no time to search for a solution right now, you can boot into the 32 bit system.  I've had a 64 bit install for 2 years and I can say that there was some tweaking involved but very little.  As stated before, it depends on what programs you are running though.

---

### Post by falkTX on 2008-04-12
What about wine?
Do x86 apps (I use a lot of FL Studio + WineASIO + Vstplugins) work on x86 wine??

---

### Post by s_raghu20 on 2008-04-14
I recently installed 64bit Hardy on my Core2Duo 2GB RAM sytem, and its working just fine.

Earlier I have been using 32 bit gutsy for quite some time (about an year or so) on the same box and it was fine (rather, getting better with updates coming through). But, this Hardy version is just so much better.

It worked out of the box. No tweaks for my piece of hardware. The performance, on the other hand, I cant really comment.

for me, the statement that the software uses all of my hardware's capabilities is good enough.  Unless there are big bombing issues with Hardy@myHardware I dont think I'd ever go back to the 32 bit version.

:)

---

### Post by mivo on 2008-04-14
> **zvacet said:**
> I´m not an expert,but I think you will feel the difference if you have >4GB of ram.In case thar you don´t plan to upgrade your hardware 32 bit should be fine.

There are many more advantages, even if you don't have 4 GB RAM. There is little reason not to run a 64-bit version on 64-bit hardware. Except Java plugins, I haven't encountered any software that wasn't available as 64-bit version, and you can of course run 32-bit software on a 64-bit Ubuntu. 

To learn more about this, [read this article]("http://www.bit-tech.net/bits/2007/10/16/64-bit_more_than_just_the_ram/1") -- ignore that it refers to Windows often, since the same applies to Linux (it's more about the general aspects anyway).

Wine works fine.

---

### Post by paperdiesel on 2008-04-14
I'm not sure why some people are posting here that their OS / games / apps are "flying" on a 64-bit O/S.  There are three main advantages to 64-bit:

1) You have more than 4 gigs of ram.  32-bit memory addressing cannot see past 4 gigs (that's 4 gigs of address space TOTAL, which means that you'll only ever see a little over 3 gigs available due to the components of the system using some of that address space).

2) Compiling.  If you are a programmer or you like to custom-compile your own apps, 64-bit will give you the option to compile your programs in 64-bit (using the -m64 switch in gcc, at least), which will compile faster.  Note that this is NOT the same as those programs RUNNING faster.  In most cases, they'll simply COMPILE faster.

3) Running programs optimized to use the extra registers in 64-bit.  If you are lucky enough to stumble upon a program that was coded to use the extra registers available in 64-bit, then yes, that program may indeed perform faster than its 32-bit counterpart.  Most of the examples of programs like these include graphics manipulation, sound manipulation, and movie manipulation.

I think that most of you talking about your favorite games / apps running faster are suffering from the placebo effect.  A 64-bit processor DOES NOT MEAN that it will perform the same computations in half the time.  It simply means that there are more memory registers available to those components and apps that know how to use them.

Just my $0.02.

---

### Post by C!pheR on 2008-04-14
I had major problems compiling Wine in 64-bit but that was back in 5.10, no idea what it would be like now. Personally I'd stick with what I have, unless you've got 4GB or more RAM.

---

### Post by mivo on 2008-04-14
> **C!pheR said:**
> I had major problems compiling Wine in 64-bit but that was back in 5.10, no idea what it would be like now. Personally I'd stick with what I have, unless you've got 4GB or more RAM.

5.10 was almost three years ago. ;)  I use Wine on a daily basis, and it works absolutely wonderful on 64-bit. No need to compile it, either, there are repositories with the 64-bit version. Like I said, have a look at [this article]("http://www.bit-tech.net/bits/2007/10/16/64-bit_more_than_just_the_ram/1"). It's not just the RAM. 64-bit is the future anyway -- almost every newly sold computer is 64-bit hardware.

---

### Post by sayakb on 2008-04-14
If you are interested in Virtualization, you might change to x64. Since all packages have their x64 alternatives, you might have an overall performance boost.. Plus, there are absolutely no problems with the x64 version (flash plugin available, no driver problem etc.)

---

### Post by falkTX on 2008-04-15
Thanks!!
I have already changed, and I had no problems.
Graphics card run perfect, my USB-Modem too, and Linux & Wine x86 programs work!!

Ubuntu on x64 rocks!

---

### Post by s_raghu20 on 2008-04-21
> **paperdiesel said:**
> 
2) Compiling.  If you are a programmer or you like to custom-compile your own apps, 64-bit will give you the option to compile your programs in 64-bit (using the -m64 switch in gcc, at least), which will compile faster.  Note that this is NOT the same as those programs RUNNING faster.  In most cases, they'll simply COMPILE faster.

3) Running programs optimized to use the extra registers in 64-bit.  If you are lucky enough to stumble upon a program that was coded to use the extra registers available in 64-bit, then yes, that program may indeed perform faster than its 32-bit counterpart.  Most of the examples of programs like these include graphics manipulation, sound manipulation, and movie manipulation.



When I compile my programs on a 64 bit OS (with the right switches etc), will it not automatically optimize the stuff to use the full power of 64 bit CPU ? 

Or, do I have to do something special to compile programs in such a way that they use the extra power supplied by a 64 bit CPU ?

really new to this area.. pls guide to the right direction...

---

