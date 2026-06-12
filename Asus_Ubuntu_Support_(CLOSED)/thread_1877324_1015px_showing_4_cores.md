---
title: "1015px showing 4 cores?"
date: 2011-11-07
forum: Asus Ubuntu Support (CLOSED)
---

### Post by iso99 on 2011-11-07
My Asus 1015px netbook is showing 4 CPUs on the System Monitor, is this normal? I only have a dual core processor :| I'm using Ubuntu Lucid, btw.

---

### Post by bluexrider on 2011-11-07
It would be strange that it would report 4 if indeed you only have 2

To check, go to the terminal and type "sudo lshw"

The results will list your hardware

ie:

*-cpu
          product:

---

### Post by clegends on 2011-11-08
It's because your processor, the n570, supports hyper-threading. Nothing unusual about this at all, just means its working. Hyper-threading is where your processor pretends (to the os) that it has 2 cores per core... thus with the dual-core n270, we appear to have 4 cores. I'm on the same machine. Enjoy it.

---

### Post by iso99 on 2011-11-13
It shows that I have 2 CPUs and 4 Logical Cores. 

After doing that command, I realized that it must have something to do with hyper-threading as what clegends have said. :)

I'll stop worrying now and enjoy it instead. I hope this is safe.

---

