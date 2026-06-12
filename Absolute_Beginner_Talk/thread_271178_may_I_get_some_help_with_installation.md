---
title: "may I get some help with installation?"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by VanDerLiviu on 2006-10-04
Hello! I am new to Linux, I read only good things about Ubuntu and I decided to use it. I got a new computer, AMD 64x 3800+, no OS installed on it. I downloaded Ubuntu Live CD and I booted from CD; instalation started, I selected the istallation option, the kernel was decompressed but then Ububtu logo appeared on the screen and that's it. Frozen...Any idea what might have gone wrong? I really woud really like to install Ubuntu...

---

### Post by WalmartSniperLX on 2006-10-04
You could check if there are errors on the disc by selecting the option on the startup. Other than that Im not sure what could cause it to fail booting. 

You got Ubuntu 6.06 Dapper Drake right?

---

### Post by whizbaby on 2006-10-04
> **VanDerLiviu said:**
>  I downloaded Ubuntu Live CD and I booted from CD; 
Which one (x86, AMD64)?
If AMD64 please first try the x86 version, the AMD64 is not recommended for beginners.

If that doesn't help, give us a hint about your hardware (drives (IDE/SATA), gfx card).

---

### Post by VanDerLiviu on 2006-10-04
Many thanks for help! Initially I tried the AMD 65 version, and later the x86 version, but I got the same result. My computer is: AMD64 (dual core), Asus M2N-E, Samsung SATA2 250 GB, Asus Extreme N7300GS/HTD. Could it be something wrong with the harddrive? In BIOs everything looks ok, as far as I can tell...](*,)

---

### Post by VanDerLiviu on 2006-10-04
Oh, I forgot to mention, yes I got Ubuntu 6.06 LTS

---

### Post by whizbaby on 2006-10-04
Yes, your HD is suspicious, but let's first try if you can boot with the *noapic* option:
When the liveCD menu shows up hit F6 and add
noapic
just before the final --

---

### Post by VanDerLiviu on 2006-10-04
Thanks a lot, whizbaby! I followed you suggestion (*noapic*) and - great! - Ubuntu started loading from CD! Now I started the installation on the hard disk, I hope everything will be all right ! Thanks again!

---

### Post by whizbaby on 2006-10-04
brainy-smurf blabber (pseudo quote):
**A**dvanced **P**rogrammable **I**nterrupt **C**ontroller can cause many problems (often caused by hardware not conforming to the official APIC standard specification) like hard lockups or devices not working properly.

---

### Post by sKuarecircle on 2006-10-04
Well congrats man, I new to Ubuntu myself, a couple of hours (never touched Linux before) and it rocks, plus the forum is helpful, search for the issue you have and you will almost always find it, if not post and someone will answer, loving it.

---

### Post by VanDerLiviu on 2006-10-05
Excellent, now I got Ubuntu installed on my desktop and is really, really great! Thanks everybody for help! :D

---

