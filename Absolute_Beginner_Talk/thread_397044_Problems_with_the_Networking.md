---
title: "Problems with the Networking"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by petru_k on 2007-03-30
Hi everybody,

I am a beginner in Linux. I have two OS on my PC, Windows XP on one HD and Ubuntu 6.06 on the other one.
The problem is that I cannot connect to the internet  on Ubuntu.
 I have a PPPoe connection type. It works very well in Windows. However in Ubuntu it does not work at all.
I have an Asus motherboard with an Nvidia K8N4 chipset and the net card is onboard. The processor is AMD 64 (I put the x86 version of Ubuntu though).

What I do know until now is that:
1. In Menu/System/Administration/Networking  I see only a modem and no ethernet card.
2. Typing ifconfig gives only a 'lo' and no 'eth0'
3. Typing ifconfig -a does not show 'eth0' either
4. It seems that Ubuntu does see somehow the ethernet, as far as I can see from Device Manager and from lspci. I may be wrong, due to my limited knowledge of Ubuntu.

So what should I do now?

Many thanks!
Peter

---

### Post by dreager on 2007-03-30
Good luck! I tried for 3 weeks and gave up. Go with Mandriva linux. They put Modem and wireless setup in ubuntu but NOT dsl....now thats retarded.

I partitioned and installed Mandriva in 10 minutes and dsl  hooked up following "dsl instructions" in 5 mins.


Lifes too short for this crap.

---

### Post by DivineOmega on 2007-03-30
It is possible the wrong driver is being loaded for your Ethernet card. Which version are you running? If you are on 6.06, try the newer 6.10 version as this may have support for your card.

---

### Post by zvacet on 2007-03-30
Is it USB you are using?If not maybe this will help you
[http://ubuntuforums.org/showthread.php?t=397196]("http://ubuntuforums.org/showthread.php?t=397196")
Read two last posts.

---

### Post by petru_k on 2007-03-30
Thanks for help. The problem has been solved.

Peter

---

