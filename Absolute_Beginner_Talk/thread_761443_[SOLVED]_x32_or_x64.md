---
title: "[SOLVED] x32 or x64?"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by crazyfuturamanoob on 2008-04-21
how do I now is my ubuntu x32 or x64?
I guess a command in terminal tells everything
so many posts but I never learn... :)

---

### Post by grokwik on 2008-04-21
your comp is 32 or 64, your OS just follows ! I guess you can see that information during the boot (but I'm not sure...)

---

### Post by crazyfuturamanoob on 2008-04-21
im too lazy to boot
does this help?
1667 MHz processor AMD Athlon 2000+ (1.7GHz)

---

### Post by bwallum on 2008-04-21
Hiya

Is your hardware 32 bit or 64 bit. The processor (cpu) will tell all. Basically any processor with pins over 700 odd will be a 64 bit. Then follow this clue by installing 32bit (x32) or 64bit (x64) Ubuntu. Installing the generic x32_x64 version will do the job for both. Just thought you might like a little more insight.

---

### Post by bwallum on 2008-04-21
you're 32 bit

---

### Post by crazyfuturamanoob on 2008-04-21
i want to get scorhced3d on my computer
via firefox but do i have to dl x32 version then?
and what happens if I have the wrong version?

---

### Post by luctor on 2008-04-21
uname -m in a terminal :-)

```

uname -m
x86_64
```

i'm running a 64 bit version

---

### Post by crazyfuturamanoob on 2008-04-21
> **luctor said:**
> uname -m in a terminal :-)

```

uname -m
x86_64
```

i'm running a 64 bit version
What the hell does this mean?
> 
i686


---

### Post by philinux on 2008-04-21
It means your 32 bit.

---

### Post by spikeJD on 2008-04-21
I'm guessing you didn't install... if you did, check the disk!:popcorn:

If your CPU is 64bit then the OS could be either 32 or 64 bit.
(If your CPU isn't 64bit then it definately will be 32bit ubuntu!)

I installed the 32bit on my AMD64 system because most software is compiled for 32bit systems.

I guess as time goes on it will become more productive to have the 64bit version installed.


:confused:I'm not sure how you find out from the commandline, try the "about" screen in gnome, or firefox, it may mention 64bit.

You could also try to apt-get install a package that isn't supported by 64bit, and wait for the "no package found" message.

---

### Post by crazyfuturamanoob on 2008-04-21
101th post :):):):)

---

### Post by bwallum on 2008-04-21
I'm running the AMD64 bit version and everything I use runs.

---

