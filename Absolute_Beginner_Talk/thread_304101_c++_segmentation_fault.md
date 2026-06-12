---
title: "c++ segmentation fault"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2006-11-21
hy guys. my question goes like this. when i compile my source everything is ok, but when i try to run it it gives me segmentation fault! i am pretty sure i've allocated all the pointers so i think it's about permisions. how can i solve that? can someone enlighten me plz? thx

---

### Post by adwait on 2006-11-21
A segmentation fault is mostly something to do with the memory...anyhow, as if as I understand, it can have nothing to do with permisssions. There must be something wrong with the code.

---

### Post by Arndt on 2006-11-21
> **adwait said:**
> A segmentation fault is mostly something to do with the memory...anyhow, as if as I understand, it can have nothing to do with permisssions. There must be something wrong with the code.

The fine tool valgrind may help.

---

### Post by dataw0lf on 2006-11-21
Use gdb to examine the core dump.

---

### Post by mendingo84 on 2006-11-21
i know it sounds stupid, but i've read about permissions on wikipedia, that's why i was asking. what is valgrind? how do i use it?

---

### Post by LLRNR on 2006-11-21
You should find valgrind in your repos, but start with [this](http://www.valgrind.org). Anyway, seg faults got nothing to do with permissions, but with screwed up programming code. The system sees something isn't ok with your code, that it tries to write at an illegal adress, so it doesn't allow your program to do so and it sends it a SIGSEGV signal, which leads to the message you got - "Segmentation fault". Now assuming you learn C++ well... it's most probable you did something wrong with those nasty pointers, haven't ya ? :lol:

Anyway, don't despair, since my OS prof tells us that: "Listen to me, I tell ya, if you ever meet someone who calls himself a programmer and says that he NEVER received a seg fault ... well I tell ya, THAT'S NOT A REAL PROGRAMMER !" :lol:

Cheers,

LLRNR

---

### Post by SneakyWho_am_i on 2008-05-26
Technically a segmentation fault can have something to do with permissions - just not (directly) filesystem permissions.

Later versions of the Linux Kernel are sometimes not allowing use of soe lower memory regions (or something, like everything under 65K, I dunno, I'm no expert)

SELinux on CentOS is a great way to keep scripts/programs from executing correctly. Which, if I understand, is through a permissions thing.

So, it's not that Segfaults can't be permission-related. It's that they can't (directly ;)) be filesystem-permissions-related. Terrible, one term referring to two things.
Can I cite a reliable source? No, but here is some output from valgrind from a segfault where it specifically mentions permissions:

```
sneaky@ubuntu:/media/imvucode$ valgrind kdeinit
==30543== Memcheck, a memory error detector.
==30543== Copyright (C) 2002-2007, and GNU GPL'd, by Julian Seward et al.
==30543== Using LibVEX rev 1804, a library for dynamic binary translation.
==30543== Copyright (C) 2004-2007, and GNU GPL'd, by OpenWorks LLP.
==30543== Using valgrind-3.3.0-Debian, a dynamic binary instrumentation framework.
==30543== Copyright (C) 2000-2007, and GNU GPL'd, by Julian Seward et al.
==30543== For more details, rerun with: -v
==30543== 
==30543== Invalid read of size 2
==30543==    at 0x400A7E1: (within /lib/ld-2.7.so)
==30543==    by 0x4003125: (within /lib/ld-2.7.so)
==30543==    by 0x40138EC: (within /lib/ld-2.7.so)
==30543==    by 0x4000C3D: (within /lib/ld-2.7.so)
==30543==    by 0x4000816: (within /lib/ld-2.7.so)
==30543==  Address 0x5c93b42 is not stack'd, malloc'd or (recently) free'd
==30543== 
==30543== Process terminating with default action of signal 11 (SIGSEGV)
==30543==  Access not within mapped region at address 0x5C93B42
==30543==    at 0x400A7E1: (within /lib/ld-2.7.so)
==30543==    by 0x4003125: (within /lib/ld-2.7.so)
==30543==    by 0x40138EC: (within /lib/ld-2.7.so)
==30543==    by 0x4000C3D: (within /lib/ld-2.7.so)
==30543==    by 0x4000816: (within /lib/ld-2.7.so)
==30543== 
==30543== Jump to the invalid address stated on the next line
==30543==    at 0x1F6: ???
==30543==    by 0x5070A6F: ???
==30543==    by 0x4003125: (within /lib/ld-2.7.so)
==30543==    by 0x40138EC: (within /lib/ld-2.7.so)
==30543==    by 0x4000C3D: (within /lib/ld-2.7.so)
==30543==    by 0x4000816: (within /lib/ld-2.7.so)
==30543==  Address 0x1f6 is not stack'd, malloc'd or (recently) free'd
==30543== 
==30543== Process terminating with default action of signal 11 (SIGSEGV)
==30543==  Bad permissions for mapped region at address 0x1F6
==30543==    at 0x1F6: ???
==30543==    by 0x5070A6F: ???
==30543==    by 0x4003125: (within /lib/ld-2.7.so)
==30543==    by 0x40138EC: (within /lib/ld-2.7.so)
==30543==    by 0x4000C3D: (within /lib/ld-2.7.so)
==30543==    by 0x4000816: (within /lib/ld-2.7.so)
==30543== 
==30543== ERROR SUMMARY: 2 errors from 2 contexts (suppressed: 64 from 1)
==30543== malloc/free: in use at exit: 0 bytes in 0 blocks.
==30543== malloc/free: 0 allocs, 0 frees, 0 bytes allocated.
==30543== For counts of detected errors, rerun with: -v
==30543== All heap blocks were freed -- no leaks are possible.
Segmentation fault
```

So yeah. It can be about permissions, but not avbout what we nromally mean when we mention "permissions". I hope this helps some future traveller.

---

