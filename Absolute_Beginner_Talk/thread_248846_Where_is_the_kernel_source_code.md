---
title: "Where is the kernel source code?"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by CeeDub on 2006-09-01
I need to install Cisco VPN client.  I've downloaded what I need, but when I try to install it it says:

> In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.

For RedHat 6.x users these files are installed in /usr/src/linux by default
For RedHat 7.x users these files are installed in /usr/src/linux-2.4 by default
For Suse 7.3 users these files are installed in /usr/src/linux-2.4.10.SuSE by default

Directory containing linux kernel source code []

I am not quite sure where it is.  I've looked around, but I'm not sure what I'm looking for.  Could someone help me?

---

### Post by bruce89 on 2006-09-01
On Dapper:
```
sudo aptitude install linux-headers-`uname -r`
```
{Adapted from post no.3}

---

### Post by Bachstelze on 2006-09-01
```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by CeeDub on 2006-09-01
Thanks for the quick response.  Will  the headers now be in /usr/src/'uname'?

---

### Post by Bachstelze on 2006-09-01
The files will be in /usr/src/linux-headers-`uname -r`, i.e. /usr/src/linux-headers-2.6.15-26 and /usr/src/linux-headers-2.6.15-26-686 if that's the kernel you have.

---

