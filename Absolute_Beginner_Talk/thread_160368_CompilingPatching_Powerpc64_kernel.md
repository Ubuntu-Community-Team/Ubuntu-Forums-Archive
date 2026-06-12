---
title: "Compiling/Patching Powerpc64 kernel"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by plush on 2006-04-14
I'd like to implement the following patches to fix a particular problem with the powerpc64 distribution of Ubuntu: 

[http://lkml.org/lkml/2006/4/12/229](http://lkml.org/lkml/2006/4/12/229)
And:
[http://lkml.org/lkml/2006/4/12/233](http://lkml.org/lkml/2006/4/12/233)

Any quick and easy, painless way to do this?  I read the wikis and posts, but there must be a simpler way.  BTW this is a vital patch.

I only need the default packages, options, etc.

---

### Post by hw-tph on 2006-04-15
The lkml server is down at the moment so I cannot look up those posts, but you cannot get around the fact that you need to:
[LIST]
[*]Download and unpack the kernel sources
[*]Patch them with the patches you want
[*]Configure the kernel (use an old .config to speed it up)
[*]Build the kernel image, preferrably using **make-kpkg** from the kernel-package package
[*]Rebuild any driver packages that depend on specific kernel versions, like nvidia and ati drivers, ndiswrapper, realtime-lsm, and so on.
[*]Install the kernel image and the driver images (if any)
[/LIST]

Håkan

---

### Post by plush on 2006-04-15
Thanks... I think I got it... it's just that those patches are for the 2.6.16 or .17 kernel, and the linux-source kernel (Ubuntu), I could only find in 2.6.15. Using make oldconfig or make xconfig with my 2.6.15-20 kernel's config doesn't seem to work; besides a few harmless stub warning, I get some kind of error involving nvram_byte  :-k  

> "ld: drivers/built-in.o section .init.text exceeds stub group size
ld: arch/powerpc/kernel/built-in.o section .init.text exceeds stub group
size
ld: init/built-in.o section .init.text exceeds stub group size
ld: net/built-in.o section .text exceeds stub group size
ld: drivers/built-in.o section .text exceeds stub group size
ld: block/built-in.o section .text exceeds stub group size
ld: security/built-in.o section .text exceeds stub group size
ld: ipc/built-in.o section .text exceeds stub group size
ld: fs/built-in.o section .text exceeds stub group size
ld: mm/built-in.o section .text exceeds stub group size
ld: kernel/built-in.o section .text exceeds stub group size
ld: arch/powerpc/platforms/built-in.o section .text exceeds stub group
size
ld: arch/powerpc/kernel/built-in.o section .text exceeds stub group size
ld: arch/powerpc/kernel/head_64.o section .text exceeds stub group size
drivers/built-in.o: In function `.platinumfb_probe':platinumfb.c:(.text
+0x84a1c): undefined reference to `.nvram_read_byte'
:platinumfb.c:(.text+0x84ac0): undefined reference to `.nvram_read_byte'
drivers/built-in.o: In function `.imsttfb_probe':imsttfb.c:(.text
+0x88344): undefined reference to `.nvram_read_byte'
:imsttfb.c:(.text+0x88368): undefined reference to `.nvram_read_byte'
drivers/built-in.o: In function `.control_init':controlfb.c:(.init.text
+0x52ec): undefined reference to `.nvram_read_byte'
drivers/built-in.o:controlfb.c:(.init.text+0x54dc): more undefined
references to `.nvram_read_byte' follow
"

---

### Post by plush on 2006-04-18
Removed

---

