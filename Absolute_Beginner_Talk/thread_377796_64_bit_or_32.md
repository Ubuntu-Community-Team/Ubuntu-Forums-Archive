---
title: "64 bit or 32?"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by jjcechva on 2007-03-06
Hi, this is my first post but I was just about to try Ubuntu (and Linux) for the first time today.  My question is this - what version should I download?  I was going to go with version 6.10.

6.10 desktop (ubuntu-6.10-desktop-i386.iso)
6.10 AMD64 (ubuntu-6.10-alternate-amd64.iso)

Basic computer specs:

AMD Athlon(tm) 64 X2 Dual
Core Processor 4600+
2.41 GHz, 1.00 GB or RAM

Thanks.:guitar:

---

### Post by OldTimeTech on 2007-03-06
Use the 32, 64 doesn't have the amount of programs to work with that the 32 bit does.  Plus the 32 bit looks blazing fast on a 64 machine ;)))

---

### Post by Brunellus on 2007-03-06
> **jjcechva said:**
> Hi, this is my first post but I was just about to try Ubuntu (and Linux) for the first time today.  My question is this - what version should I download?  I was going to go with version 6.10.

6.10 desktop (ubuntu-6.10-desktop-i386.iso)
6.10 AMD64 (ubuntu-6.10-alternate-amd64.iso)

Basic computer specs:

AMD Athlon(tm) 64 X2 Dual
Core Processor 4600+
2.41 GHz, 1.00 GB or RAM

Thanks.:guitar:
Reasons to install a 64-bit kernel:

* You have more than 4 GB of RAM

* You do a lot of processor- and memory- intensive work.

* You enjoy seeing what the future might feel like.

Reasons NOT to install a 64-bit kernel:

* You run non-free, binary-only software, notably Adobe Flash and/or any number of device drivers.

* You want to run WINE or Cedega


Advice:  run a 32 bit kernel for now.

---

### Post by steve.horsley on 2007-03-06
A third vote for 32 bit here. The 64 bit is still rough round the edges, I gather, and you will have trouble with audio/video codecs, drivers flash etc that's just not available in 64-bit. 

Learn to walk with 32-bit first.

---

### Post by steven8 on 2007-03-07
OKay, I found this thread via search, because I am building a new computer, and I'm getting a Sempron 64 bit processor.  Now, I gather from what I'm reading that I'll start out with the 32 bit Dapper.  However. . .how do I go about upping to the 64 bit in the future if it seems like it's time to do so.

---

### Post by steve.horsley on 2007-03-07
I'm afraid that's a re-install. However, if you have a separate home partition for storing your personal data and settings, you can reinstall the OS without losing personal stuff.

---

### Post by steven8 on 2007-03-07
So, it's kind of like damned if you do, damned if you don't.  Running 32 bit will give greater compatibilty, because most things are still written for 32 bit processors, yet running 32 bit underutilizes your nice new 64 bit processor.

Hmm.

---

### Post by Brunellus on 2007-03-07
> **steven8 said:**
> So, it's kind of like damned if you do, damned if you don't.  Running 32 bit will give greater compatibilty, because most things are still written for 32 bit processors, yet running 32 bit underutilizes your nice new 64 bit processor.

Hmm.
"underutilizes" is a fuzzy word.  I really don't see the point of running a 64-bit kernel unless I really needed it.  I have no machines that would really benefit, and none of my computing tasks are so intensive that they would require it.

---

### Post by SuSUntu on 2007-03-07
**Short answer:**

32- bit

**Long answer:**

I'm all for the 32-bit Ubuntu version even though I have AMD 64 machines. I have run Suse  64-bit, Centos 64-bit, and Breezy, Dapper and Edgy as 64-bit. 

With Ubuntu, it is possible to get a lot of 32-bit apps running in 64-bit Ubuntu through hacks or tweaks or voodoo (I was using a chrooted 32-bit environment in Ubuntu to get most things to work). However, some things I could never get to work properly or consistently (like Wine for example ... which is flaky enough on its own even in pure 32-bit environments).

The most perplexing thing is that when something isn't working correctly in the 64-bit version, you are faced with more questions about why it may not be working:

- is it because of a native bug in the application (meaning it would not work correctly even in pure 32-bit environments)?;
- is it because you haven't set up everything properly for the app to run in the 64-bit version?;
- or is it because it won't run in a 64-bit environment no matter what you do?

The forums here are partially helpful in answering these questions, but because there are fewer people running 64-bit Ubuntu, there are fewer resources to nail down those frustrating details holding you back.

So, after a few years of running 64-bit Ubuntu, I finally decided to wipe my 64-bit Edgy installation and start over with 32-bit just to see how different things might be. You can't imagine my elation with the ease of setting everything up compared to 64-bit ... and Wine ... which I cursed for so long ... worked immediately upon installation without throwing up a bunch of error messages.

Additionally, I have always had some complaints with Ubuntu not feeling as snappy as other distros or Windows XP while using the 64-bit version, but my 32-bit installation is really nice in that regard. While there are too many variables to attribute this newfound "snappiness" strictly to the changeover to 32-bit, it is a breath of fresh air nevertheless and a bonus if it is related to the 32-bit version changeover.

As to other speed issues when using CPU-intensive processes, I have seen test results that indicate that 32-bit retains an edge in some cases and 64-bit retains an edge in others, but in almost all cases, the difference in time-to-task-completion is so minimal between the two as not to warrant all the extra hassle one has to go through when using the 64-bit version.

Finally, I'll just mention one last side-benefit of using the 32-bit version: since things are so much easier to set up (no chroot, no compatibility layers, etc. etc), you will be more likely to take the recommended route of doing a clean install when a new version of Ubuntu comes out rather than just doing an upgrade. In other words, since the 64-bit version can be such a pain to set up depending on what software you are trying to run, you are less likely to be willing to put in the effort it would take to start over ... and that can lead to an additional question on top of the other ones I posted earlier:

- is this thing I'm trying to do not working correctly now because I upgraded the 64-bit environment instead of doing a clean install, or would it not work regardless?

I always did clean installs to eliminate that particular question, but the temptation just to do an upgrade was definitely there. 

Anyway, now when I browse the Ubuntu forum topics, I always half-smile to myself when I get to pass right over all those extra 64-Bit HOWTOS that aren't required for 32-bit users. It's definitely a load off. :)

---

### Post by shanepardue on 2007-03-07
Wow! I run 64-bit without any problems! I say run an operating system that gives you what 
you paid for in a 64-bit processor! I haven't across any issues and I run flash, non-free codecs, and
 everything else I want! What seems to be the problem you guys have encountered with the 64-bit
ubuntu?

---

### Post by Brunellus on 2007-03-07
> **shanepardue said:**
> Wow! I run 64-bit without any problems! I say run an operating system that gives you what 
you paid for in a 64-bit processor! I haven't across any issues and I run flash, non-free codecs, and
 everything else I want! What seems to be the problem you guys have encountered with the 64-bit
ubuntu?
issues:

* WINE.  If you must run Windows executables through a compatibility layer, 64-bit is out.  

* Binary-blob device drivers.  Wireless cards and graphics adaptors are the big offenders ehre.

* Flash and Java.

If you can run an entirely Free Software setup, the 64-bit kernel is definitely right for you.  But if your use profile requires any of the above. . . stick to 32.

---

### Post by shanepardue on 2007-03-07
I can see where you're coming from, but I've gotten flash and java working very easily. There are ways to get those working and they aren't hard at all. If he isn't using wine, it wouldn't make sense to ditch everything amd64 has to offer. Do you know what I mean?

---

### Post by Brunellus on 2007-03-07
> **shanepardue said:**
> I can see where you're coming from, but I've gotten flash and java working very easily. There are ways to get those working and they aren't hard at all. If he isn't using wine, it wouldn't make sense to ditch everything amd64 has to offer. Do you know what I mean?
it's the difference between "just working" and "just give me a few more hours of reading and writing to get it working."  chrooting to 32-bit Firefox for flash and java is non-trivial for a first-time installer.  I'd recommend it to someone who already was comfortable with Linux in general, but not to anyone who is installing an OS from scratch for the first time.

The advantages are underwhelming at best.  The only one that leaps out at me right away is the lifting of the 4 GB RAM barrier.  But seeing as most AMD64 machines are still sold with fewer than 2 GB of RAM, most consumers aren't even getting to the memory-adress-space limit.  Ditto filesystem sizes--I don't know too many home desktop users whose filesystems measure in the terabytes, never mind petabytes.

As to processing speed:  time-to-task-completion isn't much different.  If you're like me, and compting with a mug of coffee in one hand, then you're not really likely to notice much of a difference in performance.  If, on the other hand, you're dealing in real processor-intensive work--movie rendering, say--you might want to consider a move.

From where I sit, there's simply not that much of a compelling case to move to 64 bit kernels for the desktop.  Server administrators might want to think about it--all that RAM would be nice for database queries!--but the advantage to desktop users is small.

---

### Post by shanepardue on 2007-03-07
It took me about 15 minutes to get Java and Flash working and I'm not a Linux professional by any 
means. With the help of a howto written by a helpful forum poster, you can get those up and 
running in a matter of minutes. I just don't see enough hindrances to stop from trying, even if it is 
only a few processes that are being affected. 

I don't mean to start a war over something as simple as this though. We can agree to disagree. 
32-bit ubuntu still rocks my socks off on my 32-bit laptop.

---

### Post by SuSUntu on 2007-03-07
> **shanepardue said:**
> I can see where you're coming from, but I've gotten flash and java working very easily. There are ways to get those working and they aren't hard at all. If he isn't using wine, it wouldn't make sense to ditch everything amd64 has to offer. Do you know what I mean?

Just to focus on one aspect of my post, I had most things running without a hitch in a chroot environment, but even though it may not be brain surgery to get those things set up, it is extra effort that in my estimation, is not warranted by any benefit I derive from running the 64-bit version. In simplest terms regarding a chroot environment, it is like having to maintain 2 computer setups instead of one. If I saw measurable benefit from the 64-bit version, I would be willing to do whatever it took to maintain such a system. I see no benefit, and I doubt you can point me to any documentation that shows a 64-bit Ubuntu set-up consistently out-performs the 32-bit version.

The only benefit I got from the 64-bit version was the bragging rights to say I was running a 64-bit OS. That gets old after a while, and the practicality and reality of what that really means (which is nothing at this point) begins to take precedence over ego.

---

### Post by ruffneck on 2007-03-09
Thanks guys for helping me making up my mind - 32-bit it is then. 

I love these forums!

---

### Post by steven8 on 2007-03-09
> **ruffneck said:**
> Thanks guys for helping me making up my mind - 32-bit it is then. 

I love these forums!


Me too.  I should be getting the parts to build my new computer middle of next week!  I can't wait!!  :guitar:

---

### Post by shanepardue on 2007-03-09
Someday, you guys should at least try the 64-bit version just to see how much work it really is. Even if it is just a little speed difference, it is faster.

---

### Post by Brunellus on 2007-03-09
> **shanepardue said:**
> Someday, you guys should at least try the 64-bit version just to see how much work it really is. Even if it is just a little speed difference, it is faster.
The question really is "for what."  Again, if you do extremely processor-intensive work--audio or video encoding, for instance--you might see a real benefit.  If you need to address more than 4 GiB of RAM, you don't have a choice.  But for regular desktop work--what's the point?

---

### Post by dptxp on 2007-03-22
Run whatever suits you. 32-bit or 64-bit.

32-bit too has its problems.

Run Beryl and face system crashes.
Run Wine and Windows applications and face Virus threats.
I run Windows applications on Windows and Linux applications on Linux. Dual BOOT.
Simple, straight, no complications. No Virtual machines

I love 64-bit Edy Eft (6.10) on my laptop and I am sticking to it.
No looking back.

---

### Post by hyper_ch on 2007-03-22
Since you seem to get a new computer I guess you also get plenty of diskspace... you could seupt both 32- and 64-bit... and make /home a seperate partition. That way both can access the same user config data... and depending on what you want to do... you can boot into either one :)

---

