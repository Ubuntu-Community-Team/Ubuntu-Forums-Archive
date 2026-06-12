---
title: "Core2 Duo - use 64 bit?"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by shanzO on 2006-10-23
Ok, color me newb, but which Edgy Eft CD should I be burning to use with my brand new Core2 Duo and Abit AB9 mobo?

Thanks in advance!

---

### Post by Ozitraveller on 2006-10-23
You might find this interesting:

Core 2 Duo Support
[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

---

### Post by shanzO on 2006-10-23
I did look at that, and several other wiki pages, when getting a number of boxes with identical configs running with Edgy over the past several days.

All are running on the x86 version.

My question relates specifically to 64 bit. Is that the 'correct' version with Core2, or should I be running the other version (that's flagged on the download page "AMD") to get 64 bit with my Intel processor/s?

---

### Post by gn2 on 2006-10-23
> **shanzO said:**
> I did look at that, and several other wiki pages, when getting a number of boxes with identical configs running with Edgy over the past several days.

All are running on the x86 version.

My question relates specifically to 64 bit. Is that the 'correct' version with Core2, or should I be running the other version (that's flagged on the download page "AMD") to get 64 bit with my Intel processor/s?

64-bit is problematic at best.

I would suggest using 32-bit.

---

### Post by shanzO on 2006-10-23
> 64-bit is problematic at best.

I'll stick with 32-bit, then, which is running fine.

Anyone care to summarize the issues that make 64-bit "problematic"? 

Any notional dates for it not being so?

---

### Post by gn2 on 2006-10-23
> **shanzO said:**
> 
Anyone care to summarize the issues that make 64-bit "problematic"? 

Any notional dates for it not being so?

A summary would run to several pages, the main problem is interfacing with 32-bit applications, which means almost all software currently.

Check out the 64-bit Forum: [http://www.ubuntuforums.org/forumdisplay.php?f=134](http://www.ubuntuforums.org/forumdisplay.php?f=134)

I reckon date-wise 64-bit will be relevant only after Microsoft release a stable 64-bit OS.

So that's in five, ten, maybe fifteen years time.

Of course all Linux apps could have 64-bit versions before then, but given how much work will be involved I very much doubt it.

---

### Post by Rhubarb on 2006-10-23
I'm quite sure Core 2 Duos aren't 64 bit, they're all 32 bit.
I tried the 64bit Dapper on my Core 2 Duo at home (out of curiosity) - spat out an error saying that I don't have a 64 bit processor.
The 32 bit version runs fine, just make sure you install the 686 SMP kernel to get the most out of your dual core CPU.

---

### Post by gn2 on 2006-10-23
Core 2 Duo are 64 bit.

One day software will be too.........

But not anytime soon.

---

### Post by Rhubarb on 2006-10-23
Hmmm, maybe I'm getting confused between "Core 2 Duo" and "Core Duo"....
It'd be worse next year when they release the Core 2 Quad processors.
I prefer AMD's for x64, most of 'em (if not all) are 64 bit = no confusion.

---

### Post by nyinge on 2006-10-23
Yep, Core Duo is 32-bit low power consuption processors, mostly used in laptops.

---

### Post by Ozitraveller on 2006-10-25
Both AM2 X3800+ X2 and Core 2 Duo E6600 are 64bit.

WinXP 64bit is out, and has been for ages, there's just not 64bit Office or Visual Studio to go with it.

---

### Post by jdong on 2006-10-26
Core **2** Duo (Conroe and Merom) are 32-bit and 64-bit capable processors, like the AMD64 line.

Core Duo (Yonah) is not 64-bit capable.


You can run either the 32-bit or the 64-bit editions of Ubuntu on the Core 2 Duo. Currently, 64-bit distros still have some interoperability problems, mostly with some closed-source programs that are only available in 32-bit (such as Flash and Sun Java's Firefox plugin, also 32-bit Windows multimedia codecs) -- namely you cannot use them without applying some sort of 32-bit workaround first.

Bottom line is, with some level of effort, it's possible to work around these snags, but my personal point of view is why bother doing that if 32-bit works fine for you?

The only cases where I would prefer 64 bit is if: (1) I have a single program that needs to address multiple gigabytes of RAM. This is best done in 64-bit mode. (2) I do something specific that greatly benefits from 64-bit mode. Apart from some cryptographic routines and 3D rendering programs like POV-Ray, you're not gonna see any appreciably measurable performance difference simply by running a 64-bit Ubuntu.


Try both... especially if you're starting with a fresh install.... In the end, I preferred using 32-bit primarily but keeping a 64-bit dual-boot around just for fun.

---

