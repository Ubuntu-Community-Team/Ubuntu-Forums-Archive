---
title: "What is the difference between the generic and 386 kernel?"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2007-02-09
i see these mentioned and went to the Ubuntu web site but didn't find anything. So, what is the difference between the generic and 386 kernel?

Under what conditions is one more desirable than the other?

---

### Post by jd65pl on 2007-02-09
You wont see any difference between generic and X86 kernels, generic has replaced the 386 and smp 686 kernels.

---

### Post by Patrick K on 2007-02-09
Oh, OK so the 386 is an older kernel. Thanks.

---

### Post by jd65pl on 2007-02-09
although you should check the kernel version numbers which will look like 2.xx.xx-xx

---

### Post by reiki on 2007-02-09
Not sure if this is technically correct, but...

When I install a 386 kernel, my system doesn't use both "processors" in my dual core.

When I install a 686 kernel, system see both processors.

When I install a generic kernel I get both cores, so I'm assuming the generic kernel may be determining what is appropriate for your machine. 

Either way... installing generic means I have one less thing to think about. :)

It just works

---

### Post by jd65pl on 2007-02-09
Yes 686 suports smp (multi-processor) systems whilst 386 only supports a single processor. Generic can use either a single or muliple processors.

---

### Post by ktucker on 2007-02-09
(Not an expert: ) generic supports generic processors - for one thing it seems to detect and use dual core :-). It seems generic has obsoleted ...-smp but synaptic etc seems to want to install -smp too ? Should one do this? Or, should the package managers prevent this?

---

### Post by Toufik on 2007-02-09
Until Dapper, there was a collection of different kernel: 386 and 686 with or without smp.

From Edgy, they decide to make it simple:
* 386 for compatibility --> work on mostly all x86 (i.e. mostly all the processors) but you'll have only one core activated if you have more
* generic replaces all the different version by loading the appropriate modules at boot --> should work on all x86 with single or dual core

BUT, there seems to be some problem with the generic kernel, some computer don't boot or boot extremely slowly (several minutes). 

Conclusion, use generic, in case of problem at boot, use 386

---

