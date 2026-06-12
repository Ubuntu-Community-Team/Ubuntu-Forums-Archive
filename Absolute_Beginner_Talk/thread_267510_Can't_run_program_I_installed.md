---
title: "Can't run program I installed"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by TheMatt on 2006-09-28
I installed a program via Adept, HWInfo. No shortcut was put in the Applications Menu. And whenever I run the excutable file, like in the Run Command dialoge, clicking on it, or creating an entry in the Applications Menu, nothing happens. I have reinstalled it, but the same thing still happens. When I try to run it in the command prompt, this is what I get:
```
mattmodica@Stargate:~$ which hwinfo
/usr/sbin/hwinfo
mattmodica@Stargate:~$ cd /usr/sbin
mattmodica@Stargate:/usr/sbin$ hwinfo
> misc.2.1: ioSegmentation fault

```

---

### Post by llamakc on 2006-09-28
It should not segfault because you ran it as a regular user.

Try:

sudo hwinfo

instead.

---

### Post by llamakc on 2006-09-28
Strike that: it works just fine for me as my regular user.

I'm using Version: 13.0-5ubuntu1 on Edgy and x86 platform. You?

---

### Post by TheMatt on 2006-09-28
Kubuntu 6.06 Dapper x86.

When you installed it, did it create an entry in the Applications menu? I suspect that I have to run a command after it, like hwinfo -r for example or something like that. If it created an entry in the applications menu, what is the command in that entry?

---

### Post by llamakc on 2006-09-28
It's a commandline tool. No, it does not create an entry in the menu.

---

### Post by Albi on 2006-09-28
segfault=bad installation

try downloading it again and installing

---

### Post by llamakc on 2006-09-28
No, this is not true. Many perfectly installed pieces of software segfault due to errors that are not from a "bad installation".

---

### Post by llamakc on 2006-09-28
Have you tried running `lshw` from the commandline instead? That was installed by default on my Edgy rig.

---

### Post by TheMatt on 2006-09-29
HWInfo is not a GUI program? I thought it would be similar to the windows version. I installed CPUID, which is a command line tool, and that works fine.

lshw seems to work good. It reports everything correctly, except that it reports my graphics core clock as 100 MHz slower than it is. Also, for the CPU, it says 800 MHz for size, so I am assuming that this is refering to my FSB? It doesn't say the actual clock anywhere (not thats hard to find) though.

I have reinstalled HWInfo a couple of times and nothing has changed. I even tried to manually install the .deb package in the command line, but that didn't work.

Thanks

EDIT: I tried to run KSudoku, a game I installed, and that gives me the same message, and does nothing when I click on the Applications menu entry like HWInfo. I KNOW that is a GUI program, as it has worked before. Reinstall did nothing. :confused:

EDIT2: OK, for some reason, the command got erased from the menu entry. Now it works. I'm thinking more now that there is some command after hwinfo thats missing. In Kubuntu, isn't there supposed to be a Lost & Found category in the Apps menu where menu entries that were automaticly put in go if Linux doesn't know where to put them? I don't have that folder.

---

### Post by llamakc on 2006-09-29
cat /proc/cpuinfo

---

### Post by llamakc on 2006-09-29
I posted that before reading your additional questions: I'm unfamiliar with Kubuntu & KDE.

---

### Post by TheMatt on 2006-09-30
> **llamakc said:**
> cat /proc/cpuinfo
That does work.

I guess what I'm trying to find is a good GUI system information program that goes into a lot of detail. If you have Everest Home Edition in Windows, you know that it goes into a huge amount of detail. That is what I was looking for.

I also noticed that lshw reports my Mobile AMD Sempron as Socket A instead of Socket 754. And it says that the size of my L2 cache is 128 KB but the capacity of it is 512 KB. It seems to report some things incorrectly. I know I am being picky, but would a GUI program report things more accurately?

---

