---
title: "Compile error for sk98lin driver"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by ChangWufei on 2007-08-19
i'm having a problem running the installation of the sk98lin driver in order to configure my (currently undetected with Ubuntu 6.10) Marvell 88e8001  ethernet card - i've read through some of the other threads on this particular driver/card, but I seem to be getting something that nobody else is experiencing -

I got the sk98lin driver off of my mobo cd (no ethernet driver means SOL for apt-get update or d/ling any other drivers - I have to use my laptop for accessing these forums) and followed the instructions for the install - however when it reaches the compile stage I get an error, and this is from my install log, manually typed so formatting may be a bit off:

> +++ Compile the driver
make: Entering directory '/usr/src/linux-headers-2.6.17-10-generic'
Makefile:450: .config: No such file or directory
  Building modules, stage 2.
/usr/src/linux-headers-2.6.17-10-generic/scripts/Makefile.modpost:38: .config: No such file or directory
make[1]: *** No rule to make target '.config'. Stop.
make: *** [modules] Error 2
make: Leaving director '/usr/src/linux-headers-2.6.17-10-generic'
+++ Compiler error

I'm pretty spanking new at linux/ubuntu, so I was hoping someone could help me out - without internet, life is tough!

Thanks!

---

### Post by ChangWufei on 2007-08-19
bump ^

---

### Post by ChangWufei on 2007-08-19
anybody? please?

---

