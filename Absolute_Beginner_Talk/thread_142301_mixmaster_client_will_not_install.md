---
title: "mixmaster client will not install"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-03-10
I installed the mixmaster client a weel ago but unistalled it a few days after
now when I try again it will not install.

Unpacking mixmaster (from .../mixmaster_3.0b2-1ubuntu1_i386.deb) ...
Setting up mixmaster (3.0b2-1ubuntu1) ...
mkdir: cannot create directory `/var/lib/mixmaster/Mix': No such file or directory
dpkg: error processing mixmaster (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mixmaster
E: Sub-process /usr/bin/dpkg returned an error code (1)

lex1:-? :-?

---

### Post by meborc on 2006-03-10
hmm... try to force it :mrgreen: ... use sudo when giving the installation command... it seems it is unable to create a directory

---

### Post by lex1 on 2006-03-10
i was useing sudo

lex1:( :(

---

