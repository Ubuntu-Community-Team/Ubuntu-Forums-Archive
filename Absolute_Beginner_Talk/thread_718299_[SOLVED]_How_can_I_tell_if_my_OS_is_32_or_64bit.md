---
title: "[SOLVED] How can I tell if my OS is 32 or 64bit?"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by SloYerRoll on 2008-03-08
This has got to be the rookiest question of them all. 

How can I tell which OS I'm running? I know my whole system is 64bit ready.

Thanks,

---

### Post by Vadi on 2008-03-08
What does **uname -a** say? If it has "x86_64" in there, then you're on 64bit. Otherwise, 32.

---

### Post by igknighted on 2008-03-08
Run the command "uname -a" in the terminal.  It should tell you an architecture, either amd64/x86_64 or i686/i586/i386.  Mine says i686 (see below)

```
[fitzgid@localhost ~]$ uname -a
Linux localhost.localdomain 2.6.23.15-137.fc8 #1 SMP Sun Feb 10 17:48:34 EST 2008 **i686** athlon i386 GNU/Linux

```

---

### Post by SloYerRoll on 2008-03-08
Thanks Vadi & igk!

```
jon@ish:~$ uname -a
Linux ish 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux
```

---

