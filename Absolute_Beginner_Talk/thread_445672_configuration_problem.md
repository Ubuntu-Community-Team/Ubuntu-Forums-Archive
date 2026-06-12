---
title: "configuration problem"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by n16_vishnoi on 2007-05-16
whenever i m configuring any package everytime i m getting the same error............

configure:2842: gcc conftest.c >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory

---

### Post by Steve H on 2007-05-16
Not sure *exactly* what that error is!!

Have you installed the build-essentials from the Repository?

If you look through Synaptic there is a package called build-essentials, it is all the compilers for configuring packages, it might be something to do with that.

Hope that helps.

:)

---

### Post by alienexplorers on 2007-05-16
As Steve H said you probably need to load build-essentials.

Enter terminal and type

> sudo aptitude install build-essentials

---

