---
title: "[SOLVED] Uninstall Crossover (Important)"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by sirgogo on 2008-01-03
Hello all:

I installed Crossover, using the file install-crossover-pro-6.1.0.sh . I am pretty unsatisfied with Crossover and have been trying to uninstall it.

The problem: I cannot figure out how to uninstall crossover.

The Crossover user-guide said:
```
If you installed CrossOver Linux Professional using the
Loki installer (install-*.sh), then use the
following command to uninstall it:
 $ ~/cxoffice/bin/cxuninstall

```
but that did not work at all?! It is an invalid command?

The command to uninstall Crossover if it had been installed as a debian package also did not work.
```
$ dpkg -r crossover-pro
```
It returned saying Crossover was not installed.

How else can I uninstall and remove all components of Crossover?

Thanks in advance.

---

### Post by hyper_ch on 2008-01-03
I'd try:

```

sudo ~/cxoffice/bin/cxuninstall

```

---

### Post by sirgogo on 2008-01-04
Thanks, I it worked... kinda. So like a bunch of files were left, but thats okay, I deleted them manually.

Thanks!

---

