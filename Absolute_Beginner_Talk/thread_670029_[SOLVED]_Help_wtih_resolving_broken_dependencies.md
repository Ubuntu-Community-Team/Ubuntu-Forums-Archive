---
title: "[SOLVED] Help wtih resolving broken dependencies"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2008-01-17
I type in
```
sudo apt-get install -f
```

...and the terminal returns
```
nick@harefoot:/usr/bin$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libmpeg3hv
The following NEW packages will be installed:
  libmpeg3hv
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
Need to get 0B/114kB of archives.
After unpacking 315kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 165765 files and directories currently installed.)
Unpacking libmpeg3hv (from .../libmpeg3hv_1%3a2.1.0-1svn20080102akirad1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libmpeg3hv_1%3a2.1.0-1svn20080102akirad1_i386.deb (--unpack):
 trying to overwrite `/usr/bin/mpeg3cat', which is also in package mpeg3-utils
Errors were encountered while processing:
 /var/cache/apt/archives/libmpeg3hv_1%3a2.1.0-1svn20080102akirad1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I went into /usr/bin and deleted mpeg3cat from there, but that didn't help.

I'm lost!!!

---

### Post by mikeyphi on 2008-01-17
Two suggestions to try!
 Open a terminal and enter:
sudo dpkg -i --force-overwrite (/usr/bin/mpeg3cat)
sudo apt-get -f install

The other possible code:
sudo dpkg --configure -a

Come back with any error messages.

---

### Post by doctorbighands on 2008-01-17
I typed in
```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/libmpeg3hv_1%3a2.1.0-1svn20080102akirad1_i386.deb
```

...which gave the following output:
```
(Reading database ... 165765 files and directories currently installed.)
Unpacking libmpeg3hv (from .../libmpeg3hv_1%3a2.1.0-1svn20080102akirad1_i386.deb) ...
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/bin/mpeg3cat', which is also in package mpeg3-utils
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/bin/mpeg3dump', which is also in package mpeg3-utils
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/bin/mpeg3toc', which is also in package mpeg3-utils
Setting up libmpeg3hv (1:2.1.0-1svn20080102akirad1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```

Then, when I typed "sudo apt-get -f install", it seemed to do the trick!

So, THANK YOU!!!

---

