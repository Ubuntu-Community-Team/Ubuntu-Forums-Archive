---
title: "uname to ubuntu label/tag translator"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by ericmarceau on 2007-04-23
Is there any way of providing a tool that will map the result of "uname -a" to the corresponding Ubuntu release, i.e. Dapper Drake, Edgy Eff, Feisty Fawn, etc. ?

It is a real pain to be constantly trying to double check which build matches with which label.

Could this (or should this) type of tool be extended to the various packages that are used within Ubuntu, so as to verify whether a particular build will operate correctly?


thank you,

Eric

---

### Post by jfinkels on 2007-04-24
> **ericmarceau said:**
> Is there any way of providing a tool that will map the result of "uname -a" to the corresponding Ubuntu release, i.e. Dapper Drake, Edgy Eff, Feisty Fawn, etc. ?

It is a real pain to be constantly trying to double check which build matches with which label.

Could this (or should this) type of tool be extended to the various packages that are used within Ubuntu, so as to verify whether a particular build will operate correctly?


thank you,

Eric

I don't think uname gives any indication of which release of Ubuntu; it's not supposed to. "uname -a" will give you the kernel name, the nodename, the kernel release, the kernel version, the machine, the processor, the hardware platform, the operating system (taken from the man pages, of course :D)...none of these are specific or necessarily related to any release or distribution even. The best thing I suppose you could do is remember that Feisty ships with kernel 2.6.20, Edgy with 2.6.17, etc.

---

