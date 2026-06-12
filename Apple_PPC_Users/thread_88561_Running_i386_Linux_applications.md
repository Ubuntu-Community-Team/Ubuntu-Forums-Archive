---
title: "Running i386 Linux applications"
date: 2005-11-10
forum: Apple PPC Users
---

### Post by amklinux on 2005-11-10
Hi.

I'm a newbie in Ubuntu for PPC, so forgive me if this is a question already answered. I would like to know if it's possible to run i386 Linux applications in Ubuntu for PPC. If so, please help me!

Regards,

amklinux

---

### Post by kingler on 2005-11-17
Due to the difference in CPU instruction sets, you can not directly run the i386 program on PPC hardware. 

However, you may get the PPC version of the software using apt-get. 

If not, you can always try to re-compile the application if you have the source code.

If you don't have the source code, I guess you will have to find a CPU emulator to run the software (converting i386 instructions into PPC instructions in real time). But this could be really slow. 

[QUOTE=amklinux]Hi.

I'm a newbie in Ubuntu for PPC, so forgive me if this is a question already answered. I would like to know if it's possible to run i386 Linux applications in Ubuntu for PPC. If so, please help me!

Regards,

amklinux[/QUOTE]

---

