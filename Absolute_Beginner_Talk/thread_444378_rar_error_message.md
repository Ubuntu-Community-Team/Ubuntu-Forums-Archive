---
title: "rar error message"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by jonathan21 on 2007-05-15
I don't know what I have done but whenever I try to open rar it gives the following message

rar: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by rar)

---

### Post by taurus on 2007-05-15
How did you install rar anyway?  Did you install it with synaptic/apt-get/aptitude or by hand?

---

### Post by jonathan21 on 2007-05-15
from source or tarball

---

### Post by Cypher on 2007-05-15
Open a terminal with Applications->Accessories->Terminal and type
```

dpkg -l | grep glibc

```
and show us the results..

---

### Post by taurus on 2007-05-15
You mean you built rar from source!  I thought it's a closed source.  Just so you know, you can get unrar from the repos.

---

### Post by jonathan21 on 2007-05-15
I know but wanted to try installing from source and since then have been getting that message.

---

### Post by taurus on 2007-05-15
Are you sure you built it from source or you just unpacked the tar.gz and ran the rar command?

Make sure you are in the same directory with that rar and run this command.

```
ldd rar
```

---

### Post by jonathan21 on 2007-05-16
both comands produce no results

dpkg -l | grep glibc
ldd rar

---

