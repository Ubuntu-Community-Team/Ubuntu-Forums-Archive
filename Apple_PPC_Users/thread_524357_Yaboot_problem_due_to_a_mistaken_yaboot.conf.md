---
title: "Yaboot problem due to a mistaken yaboot.conf"
date: 2007-08-13
forum: Apple PPC Users
---

### Post by trapanator on 2007-08-13
Hi to all,

yesterday on a ubuntu feisty ppc of a my friend I have 
edited the "yaboot.conf". I have inverted the values on "Linux" and "Old" kernels but I forgot to
modify the initrd key (so the "old" kernel uses the "Linux" initrd and vice-versa).

The Result? Kernel PANIC at every boot.

So, I enter at the yaboot prompt and I type:

Risultato? Kernel PANIC ad ogni boot.

   hd:11,/boot/vmlinux root=/dev/hda11 ro

but with a kernel panic:

 VFS: Cannot open root device "hda11" or 0:0
 Please append a correct "root=" boot option
 Kernel panic: VFS: Unable to mount root fs on 0:0

How can I fix it?

---

### Post by stmiller on 2007-08-13
Boot the alternative PPC CD, and press tab at the boot to see options. Boot into the rescue mode. There you can repair yaboot, or execute a shell inside your install (and then repair yaboot manually).

---

### Post by trapanator on 2007-08-13
> **stmiller said:**
> Boot the alternative PPC CD, and press tab at the boot to see options. Boot into the rescue mode. There you can repair yaboot, or execute a shell inside your install (and then repair yaboot manually).

Thank you for the reply. One more question: how can I execute the shell inside my install?

---

### Post by stmiller on 2007-08-13
There's an option for that. Just boot into rescue mode from that alt cd, and you can choose 'execute a shell inside install' or whatever it's called. There are more threads on this in this forum section.

---

