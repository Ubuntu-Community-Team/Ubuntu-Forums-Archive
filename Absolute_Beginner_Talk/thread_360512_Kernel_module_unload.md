---
title: "Kernel module unload"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by mahy on 2007-02-13
Hi y'all, when i try to unload the snd-hda-intel kernel module, it tells it's being used. lsmod tells me it's being used by 2 processes. How can i find out which processes use it (to terminate them)? TIA.

---

### Post by Crooksey on 2007-02-13
You do know that your sound wont work when you unload this, right?

Just kill the Xserver and do it from a tty.

---

### Post by mahy on 2007-02-13
> **Crooksey said:**
> You do know that your sound wont work when you unload this, right?

Just kill the Xserver and do it from a tty.

Actually it's the other way around. My sound sometimes doesn't work, that's why i wanna remove the module (and plug it back). :)

---

