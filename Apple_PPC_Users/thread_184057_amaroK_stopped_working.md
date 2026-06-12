---
title: "amaroK stopped working"
date: 2006-05-29
forum: Apple PPC Users
---

### Post by eidex on 2006-05-29
hi, my amarok stopped working, when i start it from the shell i get the following error message:

/usr/lib/amarok/amarokapp: error while loading shared libraries: /usr/lib/libGL.so.1: ELF file data encoding not big-endian

it seems i have accidently installed a x86 lib, i removed and reinstalled amaroK via apt get but it did not help, which package contains the libGL.so.1 ?

thanks..

---

### Post by eidex on 2006-05-29
problem solved, i removed and reinstalled the libgl1-mesa package (i suppose there is a smarter way, but it worked :o)

---

### Post by linuxa on 2006-06-30
Thanks so much for posting your solution!

I ran into the same issue recently when I deleted libGL.so while trying to install my graphics drivers (don't ask :p).

reinstall libgl1-mesa worked great :D

Cheers

---

