---
title: "Intel iMac Network Hangs"
date: 2006-07-20
forum: Apple PPC Users
---

### Post by MightyE on 2006-07-20
After installation is complete, and I've booted into Dapper successfully, my network is constantly shaky.  Whenever transferring data across the network, it has a chance to totally hang up until I execute
```
ifdown eth1 && ifup eth1
```

It can happen anywhere from 1k transferred to several meg transferred.  I saw as much as 18 meg go across the wire.

From the installer/live DVD, I had no network issues, and I used this to 
```
apt-get update && apt-get upgrade
```
so that I was sure I had the latest version of everything.

Has anyone experienced this, and/or do you have any suggestions where I might go to find out more information?

I'm using the built-in wired ethernet card, static IP, iMac 20" Intel Core Duo.

---

