---
title: "Ubuntu / CoLinux working!"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by juako on 2007-06-07
I bought a big 500G disk for my data and have it joined with the previous 300G one through LVM, formatted the entire thing with XFS. As i need access to this data from windows, i have been using CoLinux and sharing it via Samba with the host.

As CoLinux default kernel hasn´t got the LVM driver compiled in, i faced a nasty kernel compilation. It took an entire night but it works now: 2.6.17.14 with colinux **and** Edgy patches (last stable patch from edgy, couldn't use feisty's cause they are for 2.6.20+).
GCC is 4.1 (feisty).

The following phases will be documented along this in a future howto i hope, being:

* installing ESD, X among other stuff
* migrating Ubuntu to loopbacks on the data area
* tuning the dual boot process etc...

**Need help at the following: **

Can someone tell me how can i generate a series of diffs between the patched and unpatched trees? It was a pain to half tune all that sources at hand, i need to back it up but i don't know how to use patch / diff more that doing "patch -p1" and watching at the .rej files! #-o

I'll appreciate help on that, thank you

Ubuntu is great! have been a slackware fanatic all my life but this is amazing!

---

