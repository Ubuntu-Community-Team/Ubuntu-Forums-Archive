---
title: "What does this System Perl daemon do?"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by ufan on 2007-03-22
Hi,
I've just installed Ubuntu 6.10 - the Edgy Eft

Here is an extract from 'top':
  4047 root      25   0 13616  10m 1168 S  0.0  0.9   0:00.02 perl  

I was wondering what this perl daemon does. (I'm assuming it is a daemon)

Cheers
ufan

---

### Post by devnulljp on 2007-03-22
Perl is a programming/scripting language

man perl

You're probably running something written in perl...

---

### Post by fdrake on 2007-03-22
did you run any *.pl file??

---

### Post by ufan on 2007-03-22
> **devnulljp said:**
> Perl is a programming/scripting language

man perl

You're probably running something written in perl...

Thanks for the reply.

Yes it is a perl program, but Ubuntu is running it itself as a daemon (notice 'root' in the first column).  I was wondering what its purpose was.

---

### Post by ufan on 2007-03-23
I found more about the process by looking in proc. 'cat /proc/pid/cmdline'
Thanks for the help.

---

