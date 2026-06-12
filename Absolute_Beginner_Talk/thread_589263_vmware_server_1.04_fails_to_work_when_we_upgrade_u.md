---
title: "vmware server 1.04 fails to work when we upgrade ubuntu from 7.04 to 7.10"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by ycsunil on 2007-10-24
I had installed vmware server 1.04 on ubuntu 7.04 and it was working fine. Yesterday I upgraded ubuntu from 7.04 to 7.10. Now, vmware server doesn't seem to work with ubuntu 7.10. It gives an error when I try to open vmware. Error is:
root@sunilc-desktop:~# vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

After this I tried to run vmware-any-any-update script to correct those errors, but ended with an error saying "unable to build vmmon module"

---

### Post by PartisanEntity on 2007-10-24
You need to reinstall VMWare, it needs to be recompiled for the new kernel in 7.10.

---

### Post by realvz on 2007-10-24
and you should try virtualbox too...it beats vmware hands down + it is open source

---

