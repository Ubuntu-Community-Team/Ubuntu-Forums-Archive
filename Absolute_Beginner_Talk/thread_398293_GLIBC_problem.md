---
title: "GLIBC problem"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by Peter1234123 on 2007-03-31
I cannot install GLIBC, from the repusteries, when i type "apt-get install glibc" (I am logged in as Root) it cannot find the package. Any help, thanks.

---

### Post by Majorix on 2007-03-31
Now that you spoke of it, I tried searching for it myself and couldn't find either.

What is going on? Anybody knows?

---

### Post by Maestro23 on 2007-03-31
Need to enable extra Respositories.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Then search for it again.

---

### Post by Majorix on 2007-03-31
I have all repos enabled. If you are talking of another repo, then please specify it so we can add it to the list.

Thanks.

---

### Post by Maestro23 on 2007-03-31
> **Majorix said:**
> I have all repos enabled. If you are talking of another repo, then please specify it so we can add it to the list.

Thanks.

What are you guys trying to install?  You might need libc6, libc6-dev.

---

### Post by nsilva on 2007-04-01
libc6 would include GLIBc, keep in mind that GLIBC 2.4 is not out yet. Im waiting on that to get pdfEdit to work,

> 
nsilva@Typhon:~$ pcheck libc6
Package: libc6
Status: install ok installed
Priority: required
Section: libs
Installed-Size: 9932
Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>
Architecture: i386
Source: glibc
Version: 2.3.6-0ubuntu20.4
Replaces: ldso (<= 1.9.11-9), timezone, timezones, gconv-modules, libtricks, libc6-bin, netkit-rpc, netbase (<< 4.0)
Provides: **glibc-2.3.5-0ubuntu1**
Depends: locales (>= 2.3.11)
Suggests: locales, glibc-doc
Conflicts: strace (<< 4.0-0), libnss-db (<= 2.2-6.1.1), timezone, timezones, gconv-modules, libtricks, libc6-doc, libc5 (<< 5.4.33-7), libpthread0 (<< 0.7-10), libc6-bin, libwcsmbs, apt (<< 0.3.0), libglib1.2 (<< 1.2.1-2), netkit-rpc, wine (<< 0.0.20031118-1), cyrus-imapd (<< 1.5.19-15), initrd-tools (<< 0.1.79), e2fsprogs (<< 1.35-7), libterm-readline-gnu-perl (<< 1.15-2)
Conffiles:
 /etc/init.d/glibc.sh c9816a0fc91156ccc4c48d62d1447c23
Description: GNU C Library: Shared libraries and Timezone data
 Contains the standard libraries that are used by nearly all programs on
 the system. This package includes shared versions of the standard C library
 and the standard math library, as well as many others.
 Timezone data is also included.
nsilva@Typhon:~$ 




---

