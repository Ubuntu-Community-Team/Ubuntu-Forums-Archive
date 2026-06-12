---
title: "Swap boot HD from one computer to another?"
date: 2007-06-07
forum: Apple PPC Users
---

### Post by MatthewMetzger on 2007-06-07
Hello,

I am wondering if you can take a hard disk from one PPC computer (older blue G4) and put it another computer (newer silver G4) and have it work without any problems. I'm running Ubuntu Dapper PPC Server LTS.

I work at a school and we just had a donation of a much nicer computer that would be a great upgrade for our library server (running koha). I have full backups of our data and even a snapshot of the entire system.

It would be great to be able to take out the hard drive stick it into the new computer, replacing it's hard drive. I've done this a few times before with Intel hardware, and it worked, but I never kept it up long enough to see if it had problems after more than a few days.

Any advice on this would be great.
thanks for your time,

Matthew

---

### Post by jargoman on 2007-06-09
With windows a definate no. With linux on the other hand maybe. It's not that big of a hardware leap. I'd give it a shot. Just don't try it with a monolothic kernel. Dapper has a modular kernel and the dapper live cd basically does the same thing. It detects hardware at boot and loads the necessary modules. I feel like I'm missing something though.

---

### Post by stmiller on 2007-06-09
If you are using the stock ubuntu powerpc kernel (and haven't made any alterations) then yes this will work. Is the newer computer dual processor?

---

### Post by MatthewMetzger on 2007-06-25
Thanks for your replies. The computer I want to move the disk to currently has OS 9 and I can't find out any information about the processor besides that it is 800 mhz. I'm fairly sure that it is a single processor.

Are there any linux tools to get system stats on PowerPC computers?

---

### Post by joninkrakow on 2007-06-26
> **MatthewMetzger said:**
> Thanks for your replies. The computer I want to move the disk to currently has OS 9 and I can't find out any information about the processor besides that it is 800 mhz. I'm fairly sure that it is a single processor.

Are there any linux tools to get system stats on PowerPC computers?

If it's running OS 9, you should be able to find in the Apple menu a program called Apple System Profiler. Calling that up should show you everything you need. 

-Jon

---

