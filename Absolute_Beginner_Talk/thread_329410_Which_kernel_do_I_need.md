---
title: "Which kernel do I need"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by agracey on 2007-01-01
I was wondering how to get a kernel for a AMD 64-bit X2 processor.

---

### Post by adaptr on 2007-01-01
That depends; if you want a 64-bit kernel, get the amd64 one; if not, get the latest one for 32 bit.

Open up Synaptic, and search for "linux-image".
Those are your choices; read them carefully to see what suits you best.

---

### Post by pseudonym on 2007-01-01
I'm assuming you want a 64-bit kernel? Best way to do it is to install the amd64 version of ubuntu.

It is possible to run a 64-bit kernel on an otherwise 32-bit system, but lots of things don't work - like nvidia drivers, iptables, and the xfs file system. Not recommended unless it's for something like a database server.

If you don't want the 64-bit kernel, just install 32-bit Ubuntu and upgrade later to the k7-smp kernel (smp because you have a dual core CPU).

---

