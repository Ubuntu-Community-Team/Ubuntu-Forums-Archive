---
title: "How do I check what are the modules compiled into the binaries in a package?"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-03-10
Eg. I have apache2 installed. How do I check if mod_proxy module has been compiled into the web server or if the module is available to be dynamically loaded?

In general, how do we go about checking if a particular module has been compiled into the binaries in the packages available in the repositaries?

Thanks !

---

### Post by goatflyer on 2006-03-10
I don't think there is a way you can see which modules are compiled in, since if they are already linked into the executable, you don't need to worry about having your own copy of the module!

I may be mistaken, but I suspect you are asking how to find out which modules are NEEDED by a particular program.  If this is the case, here is the output I got when I went to look for the dependancies in the apache2 I have installed on my system (first I went to find it)

Hope this helps.

$ which apache2
/usr/sbin/apache2
$ cd /usr/sbin
$ ldd apache2
        linux-gate.so.1 =>  (0xffffe000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7fa9000)
        libcrypt.so.1 => /lib/tls/i686/cmov/libcrypt.so.1 (0xb7f7c000)
        libpcre.so.3 => /usr/lib/libpcre.so.3 (0xb7f52000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7f3e000)
        libssl.so.0.9.7 => /usr/lib/i686/cmov/libssl.so.0.9.7 (0xb7f0e000)
        libcrypto.so.0.9.7 => /usr/lib/i686/cmov/libcrypto.so.0.9.7 (0xb7e11000)
        libaprutil-0.so.0 => /usr/lib/libaprutil-0.so.0 (0xb7dfd000)
        libldap_r.so.2 => /usr/lib/libldap_r.so.2 (0xb7dc8000)
        liblber.so.2 => /usr/lib/liblber.so.2 (0xb7dbb000)
        libdb-4.2.so => /usr/lib/libdb-4.2.so (0xb7ced000)
        libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb7cce000)
        libapr-0.so.0 => /usr/lib/libapr-0.so.0 (0xb7cae000)
        librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb7ca6000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7c84000)
        libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb7c6e000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7c5c000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7b2e000)
        /lib/ld-linux.so.2 (0xb7fbb000)
        libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb7b1b000)
        libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0xb7b06000)
        libgnutls.so.11 => /usr/lib/libgnutls.so.11 (0xb7aa3000)
        libtasn1.so.2 => /usr/lib/libtasn1.so.2 (0xb7a93000)
        libgcrypt.so.11 => /usr/lib/libgcrypt.so.11 (0xb7a47000)
        libgpg-error.so.0 => /usr/lib/libgpg-error.so.0 (0xb7a43000)
$

---

