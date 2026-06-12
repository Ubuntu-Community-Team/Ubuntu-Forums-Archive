---
title: "Help, my linux is broken!"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by skullman on 2006-08-26
hi,

i am getting an error message identical to that of the dodgy update released although ive been getting mine for three weeks.  it started when i put an ati radeon graphics card in and ever since i can only use command line and cant access gui.  ive tried following intruction on sorting out update any way but it doesnt solve the issue?

any help appreciated?

---

### Post by Tomosaur on 2006-08-26
From the command line, try this:
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

Reboot and see how things go!

---

### Post by skullman on 2006-08-26
hi cheers that worked, now back in ubuntu!  what caused that then, and why did that command fix it?  

cheers for your help, sorry still trying to learn all this!!!!!!

---

### Post by Tomosaur on 2006-08-26
It really depends to be honest. Depending on how you installed the drivers, it may have just been that xorg.conf wasn't refreshed, as it were, in order for the changes to have taken place. You kinda just have to get to know what things are related to each other, and that you need to check the settings when you change something drastic (if we're to count new drivers as drastic :P).

---

### Post by pplsicd on 2006-08-26
I have tried that dpkg-reconfigure (...) and still no good.  About every 45 days my system loses graphics capability.  the system will only boot to a login prompt.  Tiwce now I have reinstalled from scratch; video works up until I begin reinstalling apps.  (I can never be certain where or when it will break, it simply causes hours of frustrations and lost productivity.  Help would be most appreciated.  - I still can't lauch gdm.

---

### Post by djheadley on 2006-08-27
Sounds like a hardware problem to me.  Sometimes hardware will not quit suddenly (actually most of the time), but will be intermittently flakey.  I once spent so much time on a client's system that I finally told him to get a new system and I would try and transfer his data files.  THEN he tells me he has a backup!  Anyway, sometimes it would act like the motherboard, sometimes like the hard drive, etc, etc, all the way through the system.  He gave the system to me for parts (?) and I ended up just using the case - not even the power supply.

---

