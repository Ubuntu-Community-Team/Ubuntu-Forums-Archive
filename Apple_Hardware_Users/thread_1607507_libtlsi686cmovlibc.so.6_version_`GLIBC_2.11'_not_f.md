---
title: "/lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.11' not found"
date: 2010-10-27
forum: Apple Hardware Users
---

### Post by Symbolix on 2010-10-27
Hi,
I have been struggling for a while to create a stable environment under Ubuntu 8.04. But I am always getting these library problems. Each time I solve one of them, a new one appears.

Here is the error message:
/opt/hfs11.0.469/bin/hkey-bin: /lib/tls/i686/cmov/libresolv.so.2: version `GLIBC_2.9' not found (required by /opt/hfs11.0.469/bin/../dsolib/libHoudiniUT.so)

/opt/hfs11.0.469/bin/hkey-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.11' not found (required by /opt/hfs11.0.469/bin/../dsolib/libtiff.so.4)

So this is an application that I need to run. How can I install those libraries?  I never had these problems under Ubuntu 7.04 or Ubuntu 10.04. However I am stuck with Ubuntu 8.04.4 because it is the latest distro supporting ATI Catalyst 9.3, and 9.3 is the last release supporting my ATI X1600.

Before this, I used to get:
/usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found
for some other application. But I have installed those libraries and it worked at the end. I did not install them through the package manager but through the terminal.

Anyway, I think this location has what I need, but I am not sure which package to download and install:
[http://mirrors.kernel.org/ubuntu/pool/main/g/glibc/](http://mirrors.kernel.org/ubuntu/pool/main/g/glibc/)

libc6_2.9-4ubuntu6_i386.deb? or libc6-i686_2.9-4ubuntu6_i386.deb? or maybe something else?

Any ideas?
Thanks!

---

### Post by Symbolix on 2010-10-28
Nobody had this?

---

### Post by Symbolix on 2010-10-29
Ignore this, the application requesting these libs is a GCC4.4 one. So it makes sense.

---

### Post by tstex on 2010-11-15
Getting same problem. What did you do to fix this? Download a new version of Houdini?  - or change Ubuntu somehow?

---

