---
title: "general linux question"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by StOoZ on 2008-03-21
why does software requires both, the shared objects lib and also the dev ?
for example, a software may require both libssl0.9.8 and libssl-dev , but that doesn't make sense, aren't the dev one is used for development, so that should include all the necessary stuff for the program to run,isn't it?

---

### Post by Doctor Debian on 2008-03-21
Well no, because the development packages are simply additions to the main package, providing extra options and so on. They're not included in the main package to simplify things for the end user and free up space.

Doc Deb

---

### Post by Bachstelze on 2008-03-21
> **Doctor Debian said:**
> Well no, because the development packages are simply additions to the main package, providing extra options and so on.

To be more precise, they contain the development headers that are needed to *compile* programs that use the library in question (basically, they're needed for *compiling* stuff, not for *running* it). So, because Ubuntu is designed for the end-user who normally doesn't compile stuff, they're not included in the main package, but they're still available in the -dev package for the more advanced user who wants/needs to compile.

---

