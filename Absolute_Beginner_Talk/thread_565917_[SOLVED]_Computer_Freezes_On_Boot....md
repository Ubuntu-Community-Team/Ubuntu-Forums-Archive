---
title: "[SOLVED] Computer Freezes On Boot..."
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-10-02
I reinstalled Ubuntu and everything is running good now. I plan on sticking with Ubuntu, so I need to know how to troubleshoot it better. 

Sometimes it goes into a complete freeze where nothing works at all. The only thing I can do is manually shut it down. Is there any way around this?

After I manually shut it down it will freeze at 25% of my boot. I can't see what processes it's loading. 

So if I were to actually have this problem, what would be the best thing to do? It's not a 1 time freeze, it's every time after the freeze.

Any suggestions?

---

### Post by Pumalite on 2007-10-02
Is this the computer we are talking about: Acer Aspire 3680, 512 mb RAM, 80 gb hdd, Ubuntu Feisty Fawn 7.04?

---

### Post by tdrusk on 2007-10-02
> **Pumalite said:**
> Is this the computer we are talking about: Acer Aspire 3680, 512 mb RAM, 80 gb hdd, Ubuntu Feisty Fawn 7.04?
Yes.

---

### Post by Pumalite on 2007-10-02
That system is not working well. You have enough memory, so we cannot blame that. I would say re-install. What did you use to install?. Live CD?. Alternate is better. Also is good to follow these guidelines: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Burn at 4x and check for CD corruption before install.
I would also do a memtest first just to be sure.

---

### Post by tdrusk on 2007-10-02
I used a cd that Ubuntu sent me. 

It's not hanging on the install, but the actual os.

Everything is working fine and dandy right now (fresh install), but I just want to be able to fix it when it breaks.

---

### Post by Pumalite on 2007-10-02
According to louieb and the Oklahoma Rule: if you break it; you get to keep both pieces.

---

### Post by NotRoot:-) on 2007-10-02
I suspect that you can rule out everything except the hard drive and software install by booting and running from a live cd.  Have you tried that yet?

---

### Post by NotRoot:-) on 2007-10-02
One other thought for you.   cd to /var/log

/var/log$ ls -l dm*
-rw-r----- 1 root adm 23932 2007-10-02 19:52 dmesg
-rw-r----- 1 root adm 23799 2007-09-28 07:06 dmesg.0
-rw-r----- 1 root adm  7869 2007-09-26 06:58 dmesg.1.gz
-rw-r----- 1 root adm  7861 2007-09-19 12:19 dmesg.2.gz
-rw-r----- 1 root adm  7860 2007-09-09 20:13 dmesg.3.gz
-rw-r----- 1 root adm  7787 2007-09-08 07:09 dmesg.4.gz

more dmesg   will show you the boot sequence of the O/S
more demsg.0 will show you the PREVIOUS boot sequence of the O/S, which if it had the problems, may give us better clues.

---

### Post by shad0w_walker on 2007-10-02
The important question is where exactly does it lock during the install? Grub, just after the kernel loads (Just before the splash screen), at the splash screen, mid splash screen or even before grub has appeared. Knowing where you lock up should help to narrow down the possibilities.

---

### Post by tdrusk on 2007-10-03
> **shad0w_walker said:**
> The important question is where exactly does it lock during the install? Grub, just after the kernel loads (Just before the splash screen), at the splash screen, mid splash screen or even before grub has appeared. Knowing where you lock up should help to narrow down the possibilities.

It locks up on the splash screen where it says
        Ubuntu
----

^it locks up at about that area.

I just had the problem. I turned off my wireless and it went though. Is that area when it is loading internet stuff?

---

### Post by overdrank on 2007-10-03
> **fuzzyhair said:**
> It locks up on the splash screen where it says
        Ubuntu
-----

^it locks up at about that area.

Hi after the grub loads and the splash screen appears use the alt, F1 key to see what is the problem.

---

### Post by tdrusk on 2007-10-03
> **overdrank said:**
> Hi after the grub loads and the splash screen appears use the alt, F1 key to see what is the problem.
okay will do if I can reproduce it.

---

### Post by tdrusk on 2007-10-03
I was booting and pressed alt+f2. I wasn't sure if it was f1 or f2. If there's a difference I can reproduce it again and get the alt+f1.

It said
```
[28.900000] bug: soft lockup detected on cpu#0
```
I turned off my wireless and it worked...

Wahoo I figured it out!

After searching through some threads with that error, I came across people saying something about restricted headers causing the problem. I remembered that I had the restricted drivers manager which had something in it. I opened it up and unchecked the card it was trying to help me with and everything works great.

---

