---
title: "Getting a new processor"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by bfr on 2007-06-18
I have an AMD Semperon (socket AM2), and I'm thinking about upgrading to an Athlon 64.  Will everything still work properly?  Would I need to reconfigure some things?  I have Ubuntu 7.04 Feisty.

---

### Post by Slushdoot on 2007-06-18
It should be just fine.  Both are 64-bit CPUs if that's what you were worried about.  Expect a nice increase in performance. :)

---

### Post by reckless2k2 on 2007-06-18
if you are just replacing the socket with a new processor, you will be fine. it will auto-detect new hardware and i'm sure you're using a amd specific kernel. if not, you should rather than the generic. well check that, the generic might cover AMDs as well. not sure.

---

### Post by w4ett on 2007-06-18
> **reckless2k2 said:**
> if you are just replacing the socket with a new processor, you will be fine. it will auto-detect new hardware and i'm sure you're using a amd specific kernel. if not, you should rather than the generic. well check that, the generic might cover AMDs as well. not sure.

I believe the new generic kernel since Feisty replaces the K7 specific one.

---

### Post by st33med on 2007-06-18
However, the flash plugins will not work for 64-bit. I think there is some work-around in this forum. Might want to search for it.

---

### Post by bfr on 2007-06-18
So it would work?  Thanks.

st33med:  They won't?!  My Sempron is 64-bit, right?  I think I've played Flash movies on my Ubuntu computer that uses the Sempron.

---

### Post by amazingtaters on 2007-06-18
If you've got Flash running then you will be fine. There have been issues in general with getting Flash to work with Fiesty 64bit. I wouldn't worry about it, nothing will change except that things will run faster, which is a good thing.

---

### Post by bfr on 2007-06-18
OK, thanks - awesome.

Is there a terminal command that tells me what CPU specifically (what number, 2400, etc.) I'm using?

---

### Post by information_entropy on 2007-06-18
```
cat /proc/cpuinfo
```

Should give lots of info about your current CPU

---

### Post by Christopher on 2007-06-18
> **information_entropy said:**
> ```
cat /proc/cpuinfo
```

Should give lots of info about your current CPU


Nice command, is there one that will do the same thing for the motherboard?  Thank you in advance.

---

### Post by maddog39 on 2007-06-18
I think you really dont need to worry about your processor as long as its x86 compliant. I think thats true for almost any OS you use, even totally home brew ones.

---

### Post by joe.turion64x2 on 2007-06-18
Replace the processor, there won't be any problem there, not even '64 bits issues' provided you installed the 64 bits version. Think about the Athlon 64 as Sempron's big brother. The difference between them is usually the L2 cache size (smaller in the Sempron), the GHz, and the instruction set (32 bits for many Semprons, there are also 64 bits Semprons), and both 32 & 64 bits for the Athlon 64; anything else is mostly equal between them (provided they are for the same socket).

Joe.

---

### Post by bfr on 2007-06-19
OK.  So it wouldn't be a problem if the Athlon 64 I decide to get has a much higher bus speed or something, that is different than my DDR2 RAM's bus speed?

EDIT:  And I would have to get a regular Athlon 64, not an FX or x2, right?

---

### Post by w4ett on 2007-06-19
Your motherboard  bios  will give you options to adjust your bus speed and memory configuration.....If your M/B supports 64 bit processor then you should be ok....at the very worst your processor will run at a reduced speed.  If in doubt, the Mfg website will have a processor compatibility list for your board.

---

### Post by joe.turion64x2 on 2007-06-19
Most recent motherboards will automatically detect the processor and configure themselves accordingly. In fact in your motherboard's manual there should be a list of the supported processors (obviously you cannot install a 939 processor in a socket 754 motherboard).

Joe.

---

### Post by bfr on 2007-06-20
OK.  I read in the manual for my motherboard that it supports the Athlon 64 FX and the Athlon 64 x2 (besides the regular Athlon 64 and Semperon).  So that would mean that the Athlon 64 FX and x2 would work on my computer without any compatibility problems, right (just checking)?

Thanks for your help.  :)

---

### Post by Golyadkin on 2007-06-20
Yeah, and I suggest you go for the X2, because the dualcore is like a dream, it speeds up my performance in Ubuntu 64 bits so incredibly :) Because I do a lot of stuff at the same time, the dual core X2 is great. I got a AMD Athlon 64 X2 4200+ for less than 100 dollars.

---

