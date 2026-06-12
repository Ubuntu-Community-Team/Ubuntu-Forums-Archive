---
title: "Upgrade and program installation issue"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Coopa on 2007-05-06
I've recently put ubuntu 6.10 onto a friend's old laptop, i've been getting used to it but i've tried installing a few packages from the add/remove menu option but keep getting the error "not suitable for your hardware type (i386)", is this saying it's the processor that's the problem...as it says this is a pentium 3, which i would have thought was enough to install VlC, etc?

---

### Post by cotcot on 2007-05-06
Do you have the same when you use synaptic by typing ```
sudo synaptic
``` ?

---

### Post by Coopa on 2007-05-06
Synaptic will load through the command line with what you put above.

I just got this error message when i tried to refresh the available packages

```
http://gb.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz: Sub-process gzip returned an error code (1)

```

It gives me a similar message if i try to upgrade from 6.10 to 7.04 when prompted.


Edit: Have i some how installed Ubuntu for i386 architecture? Because isn't Pentium 3 the 486? :S Confused me now.

---

### Post by annda on 2007-05-06
have you per chance installed the 64-bit version of ubuntu? in that case, you might need to check the repositories...

---

### Post by annda on 2007-05-06
take a look at those two:

[https://answers.launchpad.net/ubuntu/+source/synaptic/+question/1953](https://answers.launchpad.net/ubuntu/+source/synaptic/+question/1953)
[http://ubuntuforums.org/archive/index.php/t-9944.html](http://ubuntuforums.org/archive/index.php/t-9944.html)

those threads are a bit old, but they may help you.

---

### Post by Coopa on 2007-05-06
Right, i found a fix for it, i think it was in one of those links you provided :)

I'll link to it properly when i find it but the gist of it was to change the address for the repository from http to ftp. This solved the update and installation problems with synaptic and aptitude.

---

