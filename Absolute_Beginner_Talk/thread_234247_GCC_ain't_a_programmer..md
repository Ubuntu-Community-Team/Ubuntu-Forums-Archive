---
title: "GCC ain't a programmer."
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by gruffy-06 on 2006-08-11
When I first tried to compile software on Ubuntu 6.06 LTS, I had to install the packages gcc, make and the kernel headers. When I try to compile executables from source, "configure" complains about the following:

configure: ERROR: C compiler cannot create execuatbles.
gruffy@ubuntu-gp16:~$

Is this a bug in gcc or do I need additional packages? I run gcc 4.0 with the linux 686 kernel. VMware Player is not affect by this error.

---

### Post by mcduck on 2006-08-11
so you just installed the gcc and make?

run 'sudo apt-get install build-essentials' to get everything you need for compiling :)

---

### Post by mostwanted on 2006-08-11
> **mcduck said:**
> so you just installed the gcc and make?

run 'sudo apt-get install build-essentials' to get everything you need for compiling :)

It's build-essential, no s.

---

### Post by gruffy-06 on 2006-08-13
Thanks for that! The barrier is broken.

--Gruffy--

P.S. I keep hearing about "build-essential_s_".

---

