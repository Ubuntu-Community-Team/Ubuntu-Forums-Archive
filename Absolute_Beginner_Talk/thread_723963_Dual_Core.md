---
title: "Dual Core"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by Extremeshannon on 2008-03-14
Hello all I am new to Ubuntu and I am back after a long period of not using linux. I have installed Ubuntu 710 on my laptop and have been told I am only running 1 Core. I use the command 

```
shannon@shannon-laptop:~$ uname -a
Linux shannon-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
```

I was told it should not say generic on the kernel version. All the research I have done says that is ok. But I went a head and rebuilt my kernel.Same thing. I just did a fresh install. Could any help.

Alienware Aura M7700 
AMD 3800 Daul Core
2 Gigs Ram
80 GIg HD
ATI Chipset

---

### Post by kpkeerthi on 2008-03-14
> I was told it should not say generic on the kernel version.
Incorrect. As you can see the generic kernal has SMP enabled. It should support multiple cores.

---

### Post by kpkeerthi on 2008-03-14
To check go to

1. Applications > System Tools > System Monitor

2. Open a terminal and type
```
cat /proc/cpuinfo
```

You should see two CPUs.

---

### Post by Extremeshannon on 2008-03-14
Thanks for the replies. I feel better about the the Install :) Yes they are both installed and working.

---

