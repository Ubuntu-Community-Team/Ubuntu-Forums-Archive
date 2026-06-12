---
title: "Where can I get my version kernel sources?"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by guy_l on 2007-12-14
Hi, 

I'm running Ubuntu on a virtual machine over my windows xp. I'd like to start developing some basic kernel modules, so I need the kernel source.

When I got to /lib/modules and I saw that I'm running 2.6.22-14-generic kernel. when I tried to "make modules" It failed because (I assume) I only got the kernel headers (as I saw in /usr/src).

So, In my understanding I got 2 options:

1. Find my version kernel sources. I found the 2.6.22 source, compiled my simple kernel module but the version magic was different from my kernel. I probably need  2.6.22-14-generic source exactly . I didn't find it in my apt-cache (by the way neither I found linux-tree) - And my sources.lst is fine (I guess).
2. Compile a whole-new kernel. After compiling and running a version from kernel.org, I found out that Debian distro have a patched kernel (which is compiled with make-kpkg).

So now I got the 2.6.22 source and I have doubts whether I need to install a new kernel.. what do you think?

Thanks in advance,
Guy.

---

### Post by hyper_ch on 2007-12-14
*scratch that post* ^^

---

### Post by ingvildr on 2007-12-14
To get the kernel source do this from command line
```
apt-get source linux-image-2.6.22-14-generic
```

---

### Post by zvacet on 2007-12-14
```
sudo apt-get source linux-image-2.6.22-14-generic
```

---

### Post by luka78 on 2007-12-14
Hm, i just check and i use 2.6.12-9-386 kernel. So i went to [http://www.eu.kernel.org/pub/linux/kernel/v2.6/](http://www.eu.kernel.org/pub/linux/kernel/v2.6/) and i couldn't find this source, so wich one should i download from this list and compile?

Thx

---

### Post by luka78 on 2007-12-14
anyone, i really need this info...

---

### Post by TNakos on 2007-12-14
just go system>administration>synaptic and look up kernel source

---

### Post by luka78 on 2007-12-14
It open just linux-kernel-headers and nfs-kernel-server, nothing else...

---

### Post by guy_l on 2007-12-14
great! It works 

Thanks a lot!! Usually the obvious thing to do is the solution, let alone for a kernel newbie like me

---

