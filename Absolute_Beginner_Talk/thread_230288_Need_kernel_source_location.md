---
title: "Need kernel source location"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by WChandler on 2006-08-05
I'm installing a work VPN client, this is a quote from the installation instructions:

Prerequisites
Need kernel sources installed that match the version of the Linux kernel you're running (use "uname -a" to find out).

Examples for RedHat 7.3 and Debian 3.1 respectively:
[root@mybox root]# rpm –Uvh [http://updates.redhat.com/7.3/en/os/i386/kernel-source-2.4.18-27.7.x.i386.rpm](http://updates.redhat.com/7.3/en/os/i386/kernel-source-2.4.18-27.7.x.i386.rpm)
[root@mybox root]# apt-get install kernel-source-2.6.8
-----------------------------------------------------------
I just installed 6.06.  What do I list as the kernel-source when I install the VPN?

---

### Post by lamego on 2006-08-05
The kernel source on Ubuntu is called linux-source, you can install it with:
```
sudo apt-get install linux-source
```

---

### Post by WChandler on 2006-08-05
Never mind...Searched and found a previous thread with the command:
sudo apt-get install linux-headers-$(uname -r)

Problem solved thanks to klytu.

---

