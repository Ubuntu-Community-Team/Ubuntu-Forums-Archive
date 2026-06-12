---
title: "How long does a Memtest86 v1.65 last?"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by drakebarimore on 2007-06-15
I recently assembled a new pc and have been having stability issues.  I think the problem is due to the graphics card, but since having tried three different ones, I decided to start looking else where.  

My CPU is an Intel Pentium D 935 @ 3.2 MHz and I'm using the heatsink which came with it.  The temp on the CPU has been running around 43-45 or so.  I think thats ok.

My motherboard is a MSI P6N SLI FI, and I may need to update the bios according to the manufacturer.  But I have read in many places to make that a last resort as it can casue more problems.

The DDR2 P6400 Corsair memory is a matched pair.  I read somewhere that the memory could be causeing a stability problem and it was suggested to run a Memtest86 on the ram to check it out.

I'm in the process of doing that now.  I started off with both sticks in the pc, but it kept messing up.  The screen would turn some wierd color like blue-green background and would be populated with a numeral, letter or character over and over again filling up the entire screen (like the last time it displayed the whole screen full of the number 1).

So, I decided to try one stick at a time.  I took my second stick out and ran a test on the first.  The test seems to be going ok, but it has been running for a very long time. almost 2 hours now.

How long does this test take?  And, should it have ran fine with both sticks installed? Or does it only test one at a time (in otherwords, why wouldn't it work with both sticks installed the first time?)

---

### Post by Moop on 2007-06-15
Memtest will run forever. You need to turn it off manually. Testing both sticks at once should have worked. The screen you got with all the letters and numbers was errors.  Try testing the other stick in the same slot as the first stick. If it tests fine then try the other slot. If both sticks test fine individually then maybe you do need to update the bios or slow your memory timings down.

---

### Post by drakebarimore on 2007-06-15
Thanks Moop, 

Well, it looks like there is a problem with the brand new Corsair memory,  As the test was running, the column under errs got to about 10 and I decided to go ahead and cut the power.  So, I guess that means that I have one good stick and one bad stick.  

They are meant to work independently right?  I mean it's not messing up because they're meant to run as a pair is it?

Anyway, I guess I can go and test the system using just the one stick and see if the system runs any more stable than it has been running.  

BTW,  is there anything that I could have done to break the memory?

---

### Post by Moop on 2007-06-16
Yes they should work independently and together. You really can't break the memory unless you up the voltage to much. 
It should run ok with one stick and maybe you can RMA the bad stick.

---

### Post by mcduck on 2007-06-16
Running just one test will tell you nothing. Quite often it takes long time before first errors start to appear, and after that you'll get more and more errors at increasing rate. Only absolutely borked RAM gives you errors on first cycle, and in that case you most likely would have noticed the problem even without running memtest..

Memtest should be run at least overnight if you want to be sure there's nothing wrong with your memory.

---

### Post by tgalati4 on 2007-06-16
While grounding yourself, gently clean the memory contacts with an eraser.

Try declocking your processor in the BIOS.  You should have a pick to reduce either the bus speed or the Xmultiplier on the processor.  

Run memtest overnight.  Shoot for 100 cycles.  If you pass then your system should be OK for installation of Linux.  Bring up the CPU speed, run memtest again.  If it passes, run your system at full speed.  Run memtest yet again.  If it passes then your system should be OK to run Linux at full speed.

Installing any operating system requires some minimum testing of the hardware.

Good luck.

---

### Post by Saghaulor on 2008-04-07
Why does Knoppix and I'm assuming other Linux distro's only come with Memetest86 v1.65 and not the newest stable v3.3? Is it some sort of licensing issue? Or is it more serious than that, is there a code flaw?

---

### Post by crav on 2008-04-21
> **mcduck said:**
> Running just one test will tell you nothing. Quite often it takes long time before first errors start to appear, and after that you'll get more and more errors at increasing rate. Only absolutely borked RAM gives you errors on first cycle, and in that case you most likely would have noticed the problem even without running memtest..

Memtest should be run at least overnight if you want to be sure there's nothing wrong with your memory.

Is 12 hours long enough, or should I keep going?

---

### Post by xeth_delta on 2008-04-21
If the memory is indeed damaged and covered under warranty I guess they will exchange it without problems.

For what it's worth, there are some arguments that can be passed to the kernel at boot time, so that the damaged zone is completely avoided and not used. I can look it up and post a tad later, should you be interested.

---

