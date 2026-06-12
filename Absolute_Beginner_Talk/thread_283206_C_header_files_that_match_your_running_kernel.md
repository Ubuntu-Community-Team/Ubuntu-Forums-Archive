---
title: "C header files that match your running kernel?"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by ELMIT on 2006-10-23
I try Ubuntu 6.06.1 in VMware 5.5. on XP

To get the tools installed I need to have gcc and the kernel headers. rpm did not work!

I used:

sudo apt-get install build-essential

but there is still something missing, because VMware tools reports:

Trying to find a suitable vmhgfs module for your running kernel.

None of the pre-built vmhgfs modules for VMware Tools is suitable for your running kernel. ...

What is the location of the directory of C header files that match your running kernel? [/usr/src/linux/include]

obviously it is either not installed or not the right place.

How to solve?
(I am testing ubuntu 2.6.15-27-386 for i386 and for amd64)


bye

Ronald Wiplinger

---

### Post by po0f on 2006-10-23
ELMIT,

Try:
```
$ sudo aptitude install linux-headers-`uname -r`
```

---

