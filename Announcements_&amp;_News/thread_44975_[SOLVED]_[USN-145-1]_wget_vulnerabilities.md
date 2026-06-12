---
title: "[SOLVED] [USN-145-1] wget vulnerabilities"
date: 2005-06-28
forum: Announcements &amp; News
---

### Post by Martin Pitt on 2005-06-28
===========================================================
Ubuntu Security Notice USN-145-1	      June 28, 2005
wget vulnerabilities
CAN-2004-1487, CAN-2004-1488, CAN-2004-2014
===========================================================

A security issue affects the following Ubuntu releases:

Ubuntu 4.10 (Warty Warthog)
Ubuntu 5.04 (Hoary Hedgehog)

The following packages are affected:

wget

The problem can be corrected by upgrading the affected package to
version 1.9.1-4ubuntu0.1 (for Ubuntu 4.10), or 1.9.1-10ubuntu2.1 (for
Ubuntu 5.04).  In general, a standard system upgrade is sufficient to
effect the necessary changes.

Details follow:

Jan Minar discovered a path traversal vulnerability in wget. If the
name ".." was a valid host name (which can be achieved with a
malicious or poisoned domain name server), it was possible to trick
wget into creating downloaded files into arbitrary locations with
arbitrary names. For example, wget could silently overwrite the users
~/.bashrc and other configuration files which are executed
automatically. (CAN-2004-1487)

Jan Minar also discovered that wget printed HTTP response strings from
the server to the terminal without any filtering. Malicious HTTP
servers could exploit this to send arbitrary terminal sequences and
strings which would then be executed and printed to the console. This
could potentially lead to arbitrary code execution with the privileges
of the user invoking wget. (CAN-2004-1488)

Hugo Vázquez Caramés discovered a race condition when writing output
files. After wget determined the output file name, but before the file
was actually opened (the time window is determined by the delay of the
first received data packet), a local attacker with with write
permission to the download directory could create a symbolic link with
the name of the output file. This could be exploited to overwrite
arbitrary files with the permissions of the user invoking wget.
(CAN-2004-2014)


Updated packages for Ubuntu 4.10 (Warty Warthog):

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.9.1-4ubuntu0.1.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.9.1-4ubuntu0.1.diff.gz)
      Size/MD5:    17337 d26d3048ef9dcc1a0c1eb935ebd31387
    [http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.9.1-4ubuntu0.1.dsc](http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.9.1-4ubuntu0.1.dsc)
      Size/MD5:      614 db27cc31fae83757f116680cc00b6bc1
    [http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.9.1.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.9.1.orig.tar.gz)
      Size/MD5:  1322378 e6051f1e1487ec0ebfdbda72bedc70ad

  amd64 architecture (Athlon64, Opteron, EM64T Xeon)

    [http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.9.1-4ubuntu0.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.9.1-4ubuntu0.1_amd64.deb)
      Size/MD5:   439626 d98cd39c187b7c51160dc034542c7fa3

  i386 architecture (x86 compatible Intel/AMD)

    [http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.9.1-4ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.9.1-4ubuntu0.1_i386.deb)
      Size/MD5:   425400 01464aa874e60830377f93786731d5b9

  powerpc architecture (Apple Macintosh G3/G4/G5)

    [http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.9.1-4ubuntu0.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.9.1-4ubuntu0.1_powerpc.deb)
      Size/MD5:   432242 fd4ec089d03c29537b30f4d5f5ebdf1a

Updated packages for Ubuntu 5.04 (Hoary Hedgehog):

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.9.1-10ubuntu2.1.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.9.1-10ubuntu2.1.diff.gz)
      Size/MD5:    82218 35dd343f7e922b6775148106135664bf
    [http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.9.1-10ubuntu2.1.dsc](http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.9.1-10ubuntu2.1.dsc)
      Size/MD5:      624 b643f637455eb9bf3d7c186b54e297e5
    [http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.9.1.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.9.1.orig.tar.gz)
      Size/MD5:  1322378 e6051f1e1487ec0ebfdbda72bedc70ad

  amd64 architecture (Athlon64, Opteron, EM64T Xeon)

    [http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.9.1-10ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.9.1-10ubuntu2.1_amd64.deb)
      Size/MD5:   211606 187a98a1be4918b96eabaef79f984b09

  i386 architecture (x86 compatible Intel/AMD)

    [http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.9.1-10ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.9.1-10ubuntu2.1_i386.deb)
      Size/MD5:   202350 8bce85f98e886eaf9bf213964e0b8e50

  powerpc architecture (Apple Macintosh G3/G4/G5)

    [http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.9.1-10ubuntu2.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.9.1-10ubuntu2.1_powerpc.deb)
      Size/MD5:   209098 4406b8a89a04b103d9d398798a11806b


-- 
ubuntu-security-announce mailing list
[email]ubuntu-security-announce@lists.ubuntu.com[/email]
[http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.1 (GNU/Linux)

iD8DBQFCwUYbDecnbV4Fd/IRAuceAJ9c/VEjv+tcJSWpv38bm1yS7ZNeqwCg9RIM
gaFgkMLLcFr9Wr0MptlskKE=
=YAyz
-----END PGP SIGNATURE-----

---

