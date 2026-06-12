---
title: "Qemu 0.8.2 Installation Error"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by sameer.iitg on 2007-08-09
Hi
I have just switched to Ubuntu and would like to install Qemu 0.8.2 for deploying Pint-OS for my Beginners' Operating Systems course on my system. I had done the following things :

1. installed gcc version 3.3.6
2. downloaded and extracted qemu tarball.
3. ./configure
4. make

but in this step I get the following error :

```

[-------------- Many data dumps -----------------]
/home/sameer/Desktop/qemu-0.8.2/usb-linux.c:29:28: linux/compiler.h: No such file or directory
make[1]: *** [usb-linux.o] Error 1
make[1]: Leaving directory `/home/sameer/Desktop/qemu-0.8.2/i386-softmmu'
make: *** [subdir-i386-softmmu] Error 2
```

I would be grateful if somebody can help.
thanks
sameer

---

### Post by MenZa on 2007-08-09
I hate to burst your bubble of compiling software yourself, but a newer version (0.9-ubuntu1) is available in the repositories. (Universe).

Ensure you have Universe enabled, then run *sudo apt-get update && sudo apt-get install qemu*.

---

### Post by sameer.iitg on 2007-08-09
thanks for the reply

I was just compiling software myself to see how it goes :)
and here I am struck... so i guess I will not leave :)

where do I hv to get this option universe ticked?

---

### Post by splintercellguy on 2007-08-09
From Synaptic, Packages -> Software Sources, then tick universe I think.

---

### Post by sameer.iitg on 2007-08-09
thanks a lot
but can't somebody please help me with the source compilation problem please

---

### Post by splintercellguy on 2007-08-09
There's not much reason to do the source compilation if you can just install the packages from repos. That said, I think you might be lacking kernel headers for your kernel version. You can find from repos.

---

