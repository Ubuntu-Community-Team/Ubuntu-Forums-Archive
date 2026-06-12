---
title: "Core 2 Processor Support in Standard Ubuntu"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by rca on 2008-01-25
OK,

So at this point I have installed an run both the Standard version of Ubuntu and the 64 bit version on my new Core 2 Duo PC.  My question is does the Standard version (non 64 bit) support the mutli processors like the 64 bit version does?

When I run system monitor on the standard version I only see one processor.  When I run it on the 64 bit version I see two processors.  Am I doing something wrong?

These are installations straight from the Gutsy live CD for standard and 64 bit systems.

Ron

---

### Post by nofrendo on 2008-01-25
If the system is using both cores, then it will appear in your hardware as 2 processors. Same as in the system monitor

But yeah 32 bit Ubuntu supports dual cores. I'm running it on an AMD64 x2 right now

---

### Post by rca on 2008-01-25
So I see both cores with the 64bit install but not with the 32bit install.

Do I need to make some change for the system to recognize both cores in the 32bit install?

---

### Post by paintba||er on 2008-01-25
I see both processors with 32 bit Ubuntu on my Mac with Core 2 Duo without needing to configure anything...

---

### Post by dcstar on 2008-01-25
> **rca said:**
> So I see both cores with the 64bit install but not with the 32bit install.

Do I need to make some change for the system to recognize both cores in the 32bit install?

You need to examine the System Log to see why the kernel is not recognising both cores on boot-up with 32 bit.

---

### Post by JCMS on 2008-01-25
IT uses both of my cores too. I can see it in the system monitor. I have both media, but I installed 32bits to avoid some problems.

---

### Post by Atomic Dog on 2008-01-26
I have a core2duo laptop with 32bit Ubuntu installed.  It recognized both cores right off the bat.

---

