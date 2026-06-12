---
title: "cpu frequency scaling problem"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by rigor mortis on 2007-06-26
hello everyone.
i installed ubuntu feisty fawn 7.04 32 bit a few days ago. after struggling with drivers and other settings the only problem that remains is cpu scaling. my cpu is amd 64bit +3000. 
[http://ubuntuforums.org/showthread.php?t=248867&highlight=cool+%27n+quiet&page=1](http://ubuntuforums.org/showthread.php?t=248867&highlight=cool+%27n+quiet&page=1) is a very good how to topic about that issue but when i write
```
sudo modprobe powernow-k8
```
it returns
```
FATAL: Error inserting powernow_k8 (/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k8.ko): No such device
```

at that topic many users complained about that error. so i decided to try something else. i downloaded cool 'n' quiet driver from amd's site. in the readme it tells that
"The powernow-k8.c and powernow-k8.h files should be 
placed in the arch/i386/kernel/cpu/cpufreq directory. 
The kernel will then need to be rebuilt and the system
rebooted.  Builds of the 64-bit arch/x86_64 kernel use 
the same source files."

i don't know how to rebuild kernel. i need help with that. actually i'm not sure that will work anyway but i want to scale my cpu. the sound of fans are killing me.
i enabled the cool 'n' quiet feature in bios and it was working in windoze properly.
any help will be appreciated.

---

