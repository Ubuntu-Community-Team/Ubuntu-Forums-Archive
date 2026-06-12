---
title: "Samba &amp; Python issues"
date: 2012-03-24
forum: Apple Hardware Users
---

### Post by clenny on 2012-03-24
Hello everyone. I've been trying to set it up where I can access shares on my  2.1 running Ubuntu 11.x from my Macbook 7.1. I was advised to set up a samba username and password via the terminal but get getting a 'command not found' message. From there, I accessed synaptic and tried to be sure I had all the samba components installed that I needed. At that point I kep receiving this message: 
E: python-testtools: subprocess installed post-installment script returned error exit status 1.

I then uninstalled python-testtools and reinstalled it but got the same  message. can anyone assist me with resolving these issues? Thanks in advance.

I tried to address this in the terminal and here is the output:

```
Setting up python-testtools (0.9.11-1) ...
Compiling /usr/lib/python2.4/site-packages/testtools/tests/test_with_with.py ...
  File "/usr/lib/python2.4/site-packages/testtools/tests/test_with_with.py", line 16
    with ExpectedException(ValueError, 'tes.'):
                         ^
SyntaxError: invalid syntax

pycentral: pycentral pkginstall: error byte-compiling files (37)
pycentral pkginstall: error byte-compiling files (37)
dpkg: error processing python-testtools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 python-testtools
E: Sub-process /usr/bin/dpkg returned an error code (1)


  
```

I hope this adds something useful so someone might respond.

---

### Post by clenny on 2012-04-11
It's been suggested to me that I should report this as a bug but I'm unsure how to do so. Can someone tell me how to do that? Thanks!!

---

