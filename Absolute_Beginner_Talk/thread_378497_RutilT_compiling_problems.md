---
title: "RutilT compiling problems"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by bloodychaos on 2007-03-07
i'm using ubuntu 6.06LTS, Dapper, and i'm currently trying to install RutilTv0.13 since i'm using a wireless PCI card with a Ralink RT2400/2450 chipset. i did the following and followed the 'Read me' that was in the tar file. anyways, i did the following and got the following error:

[COLOR="Red"]kay@Windy:~$ cd RutilTv0.13

kay@Windy:~/RutilTv0.13$ ./configure.sh

Your kernel sources cannot be found.

Kernel headers found. They do not match your running kernel.
kay@Windy:~/RutilTv0.13%[/COLOR]

anyone out there knows how to fix this? i tried searching for clues in the forums but i couldn't find any related posts...

---

### Post by energiya on 2007-03-07
> **bloodychaos said:**
> 
Your kernel sources cannot be found.


Install kernel sources. Search the repository for sources for your kernel.

> **bloodychaos said:**
> 
Kernel headers found. They do not match your running kernel.


Install kernel headers. Search the repository for header for your kernel.
To figure out what kernel you have, type in a terminal
```

uname -r

```

---

### Post by bloodychaos on 2007-03-10
it worked^^ thanks a bunch!:KS

---

