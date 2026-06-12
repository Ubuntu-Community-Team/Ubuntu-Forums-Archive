---
title: "Memory Usage Question"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by e30ernest on 2007-06-02
With a freshly booted machine and Beryl running, I get the following using the free command:

```

             total       used       free     shared    buffers     cached
Mem:       2075772     431556    1644216          0      11876     235784
-/+ buffers/cache:     183896    1891876
Swap:      3903784          0    3903784
```

A day later, I get:

```

             total       used       free     shared    buffers     cached
Mem:       2075772     938784    1136988          0     188380     518608
-/+ buffers/cache:     231796    1843976
Swap:      3903784          0    3903784

```

I also noticed when I am using the GUI System Monitor, my RAM usage from a freshly booted system is at 170MB.  A day later, it's at 215MB.  Sometimes it goes up to 350 on an idle system.  All I do is surf and play the occasional native game or once in a while, a game of Starcraft on Wine.  Could it be Wine is not exiting properly when I exit Starcraft?

Thanks for your answers!

---

### Post by shae on 2007-06-02
If you notice in your chart, most of the added memory are in cache and buffers.  This is completely normal.  When you close a program in linux, it goes into cache so it is ready to launch if you decide to reopen it.  It is not a bug; it is a feature.  It isn't like the extra mb is really making a dent in your 2 gigs of ram.

---

### Post by blackened on 2007-06-02
The thing you have to think about with memory is that if it's not being used, then it's being wasted. So ideally, to run at optimal efficiency, the entirety of RAM on your system should always be full as possible. This is why linux caches items in memory. Just think of it as Linux treating your unallocated memory as a ramdisk to speed up loading of items that were recently called for.

As an example, open a big program like Amarok or Firefox. Then close it. Then reopen it and watch how fast it loads compared to the first time. You should note a pretty remarkable difference.

---

### Post by e30ernest on 2007-06-03
Thanks.  Does the extra memory usage shown on the GUI system monitor count as cached too?  It's hard to tell since all it shows is "User memory" for the RAM.

---

### Post by blackened on 2007-06-03
> **e30ernest said:**
> Thanks.  Does the extra memory usage shown on the GUI system monitor count as cached too?  It's hard to tell since all it shows is "User memory" for the RAM.

The best way to tell is to compare the output of "free -m" (look at the second line "-/+ buffers/cache:", not the first) to the numbers in the system monitor. I'm fairly certain that the system monitor doesn't included these numbers in its display.

---

### Post by vasilis34 on 2007-06-03
Hi ,

I have a relevant question about memory usage and swap and since i am still a Linux newbie I thought that somebody could help. I 've checked several times my sytem monitor and while it shows a 41.5% usage of Ram the usage of swap is always 0%. In fact. i 've never seen it at an other percentage, always 0%, even when I open several apps together. Is that normal? There shouldn't be a usage to some percentage at least? Forgot to mention that my system runs normally, I don't have any serious speed problems, just asking from curiosity.

---

### Post by e30ernest on 2007-06-03
I think swapped refers to the page file in the HD.  As long as you still have RAM I don't think Ubuntu uses that.  I'm a newbie too so I could be wrong.

---

### Post by blackened on 2007-06-03
vasilis34: no that's not abnormal. I have 1GB of RAM and rarely do I use more than around 40% of that. So on a comparably setup system with 512MB of RAM, chances are that it would be unnecessary for the system to swap except under heavy loads.

The larger amounts of RAM in machines these days is what's driving the debate about swap partition sizes. Alot of people still recommend to use twice your RAM amount for your swap partition, while others say that 512MB to 1GB is plenty and to spare. With large drives becoming the norm, I think the difference is pretty negligible, but why waste it if you don't have to?

---

### Post by vasilis34 on 2007-06-03
Thx for the replies.
@Blackened : That was the reason I made the question. I mean the swap size. Because I made my first "real" (not on VMware) installation of ubuntu a week ago and I had a dilema about the size. So, after reading various opinions and since I have plenty of hard disk space I choosed a swap size about 2Gb on 756MB of RAM, just in case!!. Seems that i can repartition it when a space need will arise.

---

### Post by caro on 2007-06-05
> **blackened said:**
> The thing you have to think about with memory is that if it's not being used, then it's being wasted. So ideally, to run at optimal efficiency, the entirety of RAM on your system should always be full as possible. This is why linux caches items in memory. Just think of it as Linux treating your unallocated memory as a ramdisk to speed up loading of items that were recently called for.

As an example, open a big program like Amarok or Firefox. Then close it. Then reopen it and watch how fast it loads compared to the first time. You should note a pretty remarkable difference.

Great answer.  I just bought a new laptop with Ubuntu and since I heard that Ubuntu (and Linux in general) is more efficient than Windows, I worried when I saw the ***[COLOR="Blue"]free -m[/COLOR]*** command showed that I was using 485M out of my 512M.  Thanks for the explanation.

---

### Post by blackened on 2007-06-06
> **caro said:**
> Great answer.  I just bought a new laptop with Ubuntu and since I heard that Ubuntu (and Linux in general) is more efficient than Windows, I worried when I saw the ***[COLOR="Blue"]free -m[/COLOR]*** command showed that I was using 485M out of my 512M.  Thanks for the explanation.

I'm pretty sure Windows uses memory in a similar fashion, just that the utilities in Windows only display the amounts of memory in active use. Glad you found the information handy though.

---

