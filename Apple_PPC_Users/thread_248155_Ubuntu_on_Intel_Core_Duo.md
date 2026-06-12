---
title: "Ubuntu on Intel Core Duo"
date: 2006-08-31
forum: Apple PPC Users
---

### Post by David Angel on 2006-08-31
I own a MacBook with 2GHz Intel Core Duo, and I recently got a copy of ubuntu 6.06 which I wish to install on it. I tested it on LiveCD and it worked just fine (a bit slow, actually), and then a question striked me:  Does ubuntu 6.06 PC version take advantage of both processing cores or does it work only with one?  I need to know because the difference in performance would be enormous.

---

### Post by frigaut on 2006-08-31
That fact that it's slow with the live CD is no surprise. It's got to access the CD/DVD instead of the HD. It's much faster once installed.

By default, I find that it doesn't recognized that there are 2 CPU, so will use ony one of them. You have several solutions to make it see both CPU: the simplest is probably to install the 4.6.15-26-686 kernel image and enable smp explicitely in lilo.conf:
append="quiet smp"

(I have a macbook pro).

---

### Post by hajk on 2006-09-01
After the initial install of Ubuntu on the HD of your MB you need only upgrade to the 686-kernel, which is SMP-enabled by default. Ubuntu will then use both cores, no need for a boot option in LILO. Looking for a HOWTO on dual-booting Ubuntu and OS X on a MacBook using the rEFIt boot menu? Then have a look at my site [http://www.xs4all.nl/~hajk]("http://www.xs4all.nl/~hajk").

---

