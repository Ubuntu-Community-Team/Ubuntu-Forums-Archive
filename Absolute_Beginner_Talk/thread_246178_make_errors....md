---
title: "make errors..."
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by droogy on 2006-08-28
Can anyone make sense of these errors from make install?

```
make[1]: Entering directory `/home/andrew/Desktop/libexif-0.6.13/doc'
make[2]: Entering directory `/home/andrew/Desktop/libexif-0.6.13/doc'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: *** No rule to make target `install-apidocs', needed by `install-data-local'.  Stop.
make[2]: Leaving directory `/home/andrew/Desktop/libexif-0.6.13/doc'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/andrew/Desktop/libexif-0.6.13/doc'
make: *** [install-recursive] Error 1

```

There is more output from make but this is the only part that contained errors and I believe therefore is the part that is not allowing libexif to install.

---

### Post by Toxicity999 on 2006-08-28
I'm not a compiling guru, but to me that looks like a code problem, and not a dependancy issue... By all means correct me if I'm wrong.

---

