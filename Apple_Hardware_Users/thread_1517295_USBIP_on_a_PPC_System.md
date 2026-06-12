---
title: "USB/IP on a PPC System"
date: 2010-06-24
forum: Apple Hardware Users
---

### Post by PunMaster on 2010-06-24
I am running Ubuntu 10.04 on a PPC iBook. I want to use USB/IP on this system to host a USB device. I tried doing this on an x86 Ubuntu 9.10 system, and all it took to make it work was installing the "usbip" package and modprobe'ing the kernel module. On the PPC system though, the modprobe fails saying it cannot find the module. I tried separately building the module, but there were compile-time errors which I traced to my kernel being too new. Further searching led me to the "staging" kernel tree, which, if understand it correctly, contains experimental pieces of the kernel which are not put into production kernels by default. It seems, then, that the x86 Ubuntu kernel has been built with the USB/IP modules, while the PPC kernel has not. So, if I want this to work, what do I need to do? Can I just build the modules I need separately, or do I need to rebuild my kernel? In either case, where do I get the files I need and how, specifically, do I build them? I am relatively new to Linux, so please pardon my ignorance. Thank you! :)

---

### Post by PunMaster on 2010-06-26
Bump?

Does anyone have any ideas here? Is this the correct place to post this question? I am sorry if I did something wrong.

Thanks! :)

---

### Post by 3rdalbum on 2010-06-27
> **PunMaster said:**
> Bump?

Does anyone have any ideas here? Is this the correct place to post this question? I am sorry if I did something wrong.

Thanks! :)

You haven't done anything wrong, and this is the correct forum. Your situation is probably very unique and I bet nobody else here has even noticed the same problem you're having. I certainly wouldn't know where to begin.

Let's hope me bumping your topic brings this to the attention of someone who does know; otherwise you could try giving as much information about your problem (terminal outputs etc) to the subforum on Compiling Software.

---

