---
title: "Installing x64 vs x86 Versions of Ubuntu"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-09-10
i originally thought that you could only install the x64 version of ubuntu on 64-bit PC's, but then i found out a little site called [www.system76.com]("http://www.system76.com") which says otherwise.  they install the x86 version on AMD 64 processors.

so, how come when some people try to install the x86 version on a 64-bit PC, the installation process doesn't work?

also, what kernel does the default x64 version install?  the 386 kernel or what?

---

### Post by David Corrales on 2006-09-10
AMD and Intel 64bit processors (excluding the itanium line) are x86 backwards compatible. They can execute 32bit instructions.

---

### Post by fragos on 2006-09-10
There are benifits of running an x86 kernel on a 64 bit machine.  Some applications like flash player are only available in 32 bit versions.  Tricks can be performed to over some of these issues but they can be "tricky" to set up.  Many find it easier to just run the x86 distrobutions.  32 bit addressing will allow access to up to 4GB of memory.  More than an individual user needs.  Servers of course are another story and might require 64 bit addressing because more than 4GB of memory is required.

---

### Post by DarkPCTroll on 2006-09-10
Thank you fragos.

I knew a little about the x64 technology but not the complete background about the 64bit OS editions. 

**_Dark PC Troll_**

---

### Post by simonn on 2006-09-11
> **fragos said:**
> 32 bit addressing will allow access to up to 4GB of memory.  More than an individual user needs.

"640K ought to be enough for anybody."

Go with 32bit, it will make life easier. There is not a lot of benefit in going with x64.

Keep in mind that the 386 chip, Intel's first 32 bit microprocessor, was released in 1986. It took until the release of W2K for 16 bit to be ditched completely - Win 3.X was 16 bit, Win9X/ME was 32/16 bit hybrid. Yes, NT is 32 bit but was no more mainstream than 64 bit windows/linux/unix.

Expect the 64 bit to be the norm in 5 to 10 years :).

---

### Post by user1397 on 2006-09-19
so what's the kernel name for an ubuntu64
 install?  like for example in an ubuntu32 install, the default kernel is called "kernel 2.6.15-27-386"
can someone that has ubuntu64 find this?  it can be found in synaptic if you type in "linux image" i guess.

---

### Post by Brunellus on 2006-09-19
> **erik1397 said:**
> so what's the kernel name for an ubuntu64
 install?  like for example in an ubuntu32 install, the default kernel is called "kernel 2.6.15-27-386"
can someone that has ubuntu64 find this?  it can be found in synaptic if you type in "linux image" i guess.
amd64

---

