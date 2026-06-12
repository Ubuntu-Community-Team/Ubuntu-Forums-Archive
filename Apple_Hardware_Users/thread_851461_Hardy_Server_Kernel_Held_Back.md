---
title: "Hardy Server Kernel Held Back?"
date: 2008-07-06
forum: Apple Hardware Users
---

### Post by tweak on 2008-07-06
I've recently installed Hardy Server onto a Dual G5 box to act as a local sandbox webserver for our dev team, and notice that when running apt-get upgrade, 3 kernel packages are always held back. They are:

* linux-image-powerpc64-smp
* linux-powerpc64-smp
* linux-restricted-modules-powerpc64-smp

Having never used the server variant of ubuntu before this is a bit foreign to me - is there some best-practice for holding back kernel files on a server install until some situation arises this where they will be upgraded?

I've only ever come across held packages once before on an edgy desktop years ago, and that situation was related to some customisation I'd done to a specific package - the type of customisation I haven't done on these kernel files.

Can anyone shed some light on this situation?

---

### Post by cyberdork33 on 2008-07-08
I get those all the time. after doing 'sudo apt-get upgrade', you should also do 'sudo apt-get dist-upgrade to get the held packages.

---

### Post by tweak on 2008-07-08
> **cyberdork33 said:**
> I get those all the time. after doing 'sudo apt-get upgrade', you should also do 'sudo apt-get dist-upgrade to get the held packages.

Ahh you're a star. Cheers buddy!

---

