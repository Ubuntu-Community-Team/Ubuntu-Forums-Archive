---
title: "virtual machines"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by Sniper99 on 2007-01-15
ok, so i have vmware player....and i dont know how to use it, is it good to use or should i get wine......help or a walkthrough would be appreciated

---

### Post by Sniper99 on 2007-01-15
ok, i tried app get install wine, and nothing happened, does anybody have any advice

---

### Post by carlosfocker on 2007-01-15
Have you tried Xen?  Its much faster than vmware player.

Easy on 6.10:
[https://help.ubuntu.com/community/XenVirtualMachine/XenOnUbuntuEdgy](https://help.ubuntu.com/community/XenVirtualMachine/XenOnUbuntuEdgy)

For 6.06:
[http://www.howtoforge.com/xen_3.0_ubuntu_dapper_drake](http://www.howtoforge.com/xen_3.0_ubuntu_dapper_drake)

Getting windows to work:
[http://www.xensource.com/files/xen_install_windows.pdf](http://www.xensource.com/files/xen_install_windows.pdf)

---

### Post by Sniper99 on 2007-01-15
which one should i get, the open source?

---

### Post by carlosfocker on 2007-01-15
what version of Ubuntu you running?

---

### Post by Sniper99 on 2007-01-15
6.06,

---

### Post by carlosfocker on 2007-01-15
[http://www.xensource.com/download/dl_304tarballs.html](http://www.xensource.com/download/dl_304tarballs.html)

Not sure what process you have.

Truthfully tho, its much easier installing Xen on Edgy.

---

### Post by halitech on 2007-01-15
> **Sniper99 said:**
> ok, i tried app get install wine, and nothing happened, does anybody have any advice

I think it should be
```

sudo apt-get install wine

```

or  you can grab automatix and use it to install wine

---

### Post by Sniper99 on 2007-01-15
ok, this is what happened, i dont know wut to do...


spencer@spencer-desktop:~$ sudo apt-get install wine
Password:
Reading package lists... Done
Building dependency tree... Done
wine is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up clamav-base (0.88.4-1ubuntu1~dapper1) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 clamav-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
spencer@spencer-desktop:~$

---

### Post by MrKlean on 2007-01-15
IMHO they're 2 different programs, but you can install wine with the Synaptec Package Manager.  Depending on what you want to do will tell you the best program to use

---

