---
title: "What if I am using the wrong kernel?"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by daacosta on 2006-02-16
Oh well...

Here it is:

```

daacosta@ubuntu:~$ uname -a
Linux ubuntu 2.6.12-10-386 #1 Mon Jan 16 17:18:08 UTC 2006 i686 GNU/Linux
daacosta@ubuntu:~$

```

What is going on?  I am using the kernel for a 386 on a 686 processor?

I honestly need to know where to get the right version of Ubuntu with a kernel for a 686 processor.  Can a guru from this planet show me please?

I do not want to use the wrong kernel on my computer!

:mrgreen:

---

### Post by bartbes on 2006-02-16
Actually it doesn't matter, you can get a slight speed increase if using the 686 kernel, but if you don't need it, don't use it I would say. Anyway you can get it with ```
sudo apt-get install linux-686
```

---

### Post by nickle on 2006-02-16
I found little or no difference with the K7 kernel for my AMD athlon vs the i386 kernel.
If you want to test the different kernels, install them as above and choose the one you want to use in the GRUB menu.

---

### Post by LordBug on 2006-02-16
the "386" kernel/software is just the generic "I'll run on any x86 system!" version.  Generic binary versions vs. optimized custom compiled version yields, from what I've seen, practically nothing.

Honestly, I wouldn't sweat this much.  You probably won't see a speed boost using the 686 version over the 386 version.

---

### Post by jeremy on 2006-02-16
Where you definately will notice a difference is memory, the i386 kernel can only use 768Mb of RAM, so if you have more than that you should definately install i686.

---

### Post by az on 2006-02-16
[QUOTE=jeremy]Where you definately will notice a difference is memory, the i386 kernel can only use 768Mb of RAM, so if you have more than that you should definately install i686.[/QUOTE]
I beleive one of the new features that Breezy had "under the hood" is the ability to use up to 4 Gigs of ram with the stock 386 kernel.

---

### Post by arctic on 2006-02-16
[QUOTE=jeremy]Where you definately will notice a difference is memory, the i386 kernel can only use 768Mb of RAM, so if you have more than that you should definately install i686.[/QUOTE]The amount of RAM available has afaik nothing to do with the architecture you compile against but with the kernel patching you do. I have e.g  1 GB Ram being fully detected and used on my fedora box, which sports a i386 kernel, others even run 3GB and more with a "normal" i386 kernel.

---

### Post by daacosta on 2006-02-17
[QUOTE=bartbes]Actually it doesn't matter, you can get a slight speed increase if using the 686 kernel, but if you don't need it, don't use it I would say. Anyway you can get it with ```
sudo apt-get install linux-686
```[/QUOTE]

Thank you... Now my boy has the right kernel... :)

---

