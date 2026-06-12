---
title: "Xen......help needed"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by Ashrael on 2007-01-14
I was following this howto :  [http://www.howtoforge.com/xen_3.0_ubuntu_dapper_drake](http://www.howtoforge.com/xen_3.0_ubuntu_dapper_drake)

Did it al...Up to 2.3  then rebooted, did....xm list....and got:

Traceback (most recent call last):
  File "/usr/sbin/xm", line 8, in ?
    from xen.xm import main
  File "/usr/lib/python/xen/xm/main.py", line 51, in ?
    from xen.util import security
  File "/usr/lib/python/xen/util/security.py", line 25, in ?
    from xen.lowlevel import acm
ImportError: libxenctrl.so.3.0: cannot handle TLS data

Whats wrong here?

---

### Post by carlosfocker on 2007-01-14
You need TLS-capable glibc.

Also just so you know installing xen on Edgy is a breeze

[https://help.ubuntu.com/community/XenVirtualMachine/XenOnUbuntuEdgy](https://help.ubuntu.com/community/XenVirtualMachine/XenOnUbuntuEdgy)

---

