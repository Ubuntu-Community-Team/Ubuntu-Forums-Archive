---
title: "Problems Installing PPTPD"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by eolatunde4 on 2008-03-24
I am trying to get my ubuntu server to run as a vpn server using pptpd.  I was using the webmin interface to install it the first time and I didn't know that my external cd-rom was not connected.  I accidentally clicked on something else in the middle of installation, now when ever I try to install I get the following message:

```

emmanuel@unpsys2:~$ sudo apt-get install pptpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  bcrelay
The following NEW packages will be installed:
  bcrelay pptpd
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
2 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

```

I've tried the following but it gave the same message: 
```
sudo apt-get remove pptpd
```
Any help on fixing this would be great.

---

### Post by eolatunde4 on 2008-03-24
I fixed my own problem.  It took a simple reboot of the ubuntu box to fix! :lolflag:

---

