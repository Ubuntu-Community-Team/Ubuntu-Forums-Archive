---
title: "Confusion about requirements for building kernel module"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by rdilliker on 2006-09-21
I posted this in the Programming forum but got no responses so hopefully someone here can answer this:

I'm trying to learn how to write device drivers for Linux and am reading O'Reilly's book on the subject. I am just starting out but am a little bit confused because of the following excerpt:

> 
Regardless of the origin of your kernel, building modules for 2.6.x requires that you have a configured and built kernel tree on your system. This requirement is a change from previous versions of the kernel, where a current set of header files was sufficient. 2.6 modules are linked against object files found in the kernel source tree; the result is a more robust module loader, but also the requirement that those object files be available.


1)From reading some other threads on these forums it seems that having the linux kernel headers _is_ sufficient. What am I missing here that is causing confusion?

2) There is a linux-kernel-headers package and a linux-headers package. From what I can tell linux-kernel-headers has the headers for user space applications whereas linux-headers has the headers needed for kernel modules. If this is true, isn't the naming of the packages a bit confusing? I would think linux-kernel-headers means for kernel space applications.

I was able to successfully build and load the "hello world" kernel module in the book by just getting the linux-headers package so this adds to my confusion about what is stated in the book. I don't need a built kernel source tree. Anyone care to answer my questions above?

Thanks for any help.

---

### Post by MWAAAHAAA on 2006-09-21
Since this is the "Absolute Beginner Talk" forum, I would not wait for an answer on those questions here. As they are kernel specific, why don't you try the linux kernel mailing list. Check out [http://www.kernel.org/](http://www.kernel.org/)

---

