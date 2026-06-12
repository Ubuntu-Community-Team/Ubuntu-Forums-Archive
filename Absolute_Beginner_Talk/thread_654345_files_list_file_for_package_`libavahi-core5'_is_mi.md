---
title: "files list file for package `libavahi-core5' is missing final newline"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by abben on 2007-12-31
Was going to reinstall totem... got this:

```
(Reading database ... dpkg: error processing totem (--remove):
 **files list file for package `libavahi-core5' is missing final newline**
Errors were encountered while processing:
 totem
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So... where exactly is libavahi-core5, and can I just nano it or should I replace it?

thanks.

---

### Post by LinuxIsInnovation on 2007-12-31
Avahi is a framework for DNS Service discovery. This discovers connected computers/printers within the network.

---

### Post by abben on 2007-12-31
Thanks. I was able to locate the package, but I get the same error when I try to re-install that package! And if I force a complete removal (as opposed to a reinstall) of the package, I can only do so if I want to get rid of xubuntu-desktop as well. frustrating.

---

