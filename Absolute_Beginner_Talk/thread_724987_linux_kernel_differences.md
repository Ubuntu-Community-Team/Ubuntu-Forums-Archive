---
title: "linux kernel differences"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by impersonator on 2008-03-15
Hi,

My list of possible boots is filled with several different kernel versions like:
Ubuntu hardy (development branch), kernel 2.6.24-12-generic
Ubuntu hardy (development branch), kernel 2.6.24-10-generic
Ubuntu hardy (development branch), kernel 2.6.24-8-generic
Ubuntu hardy (development branch), kernel 2.6.24-5-generic
etc.

What are the differences between these?
Is one of these the stable version?
Why so many options?

Thanks!

---

### Post by oliviacond on 2008-03-15
all of them are stable (quite, not sure about hardy) version 
new kernel contain security updates, bug fixes, etc

there are many version so that you can choose between them,
for example,
sometimes using -12 may have some bug, so you choose -10.
but this is just a rare case.

my advice, use the latest.

---

### Post by impersonator on 2008-03-15
thanks!

---

### Post by sayakb on 2008-03-15
Whats the latest kernel for Gutsy??
I seem to have 2.6.22.14 version..

---

### Post by forrestcupp on 2008-03-15
You're using Hardy testing right now.  When you use an alpha or beta version of Ubuntu, you will end up with tons of kernels because they're trying to tweak it and get it ready for the final.  So they will release a new kernel very often for testing.  When the final is released, you won't see new kernels like that, they'll stick with the same one and just have minor updates that won't break your system.

As long as your system boots ok, you can just use the default one, which will be the newest one.  If you get a kernel update that causes you not to boot, just choose an older version that worked.  The main reason your system would break with a kernel update is because of proprietary drivers.  Don't be crazy enough to use Envy during testing.

Edit:
If you get tired of having all of those kernel options, you can edit some of the entries out of /boot/grub/menu.lst.  I would keep at least the last 2 kernels during testing time, though.

---

