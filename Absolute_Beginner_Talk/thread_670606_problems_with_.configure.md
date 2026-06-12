---
title: "problems with ./configure"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by poordamnedfool on 2008-01-17
here is the output

root@GoatServer:/home/jqaskwig/samba-3.0.28/source# ./configure
SAMBA VERSION: 3.0.28
LIBREPLACE_LOCATION_CHECKS: START
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
LIBREPLACE_LOCATION_CHECKS: END
LIBREPLACE_CC_CHECKS: START
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

---

### Post by RomeReactor on 2008-01-17
Hi. Do you have build-essential installed?
```
sudo aptitude install build-essential
```

---

### Post by poordamnedfool on 2008-01-17
nope that will proly do the trick, this is a bare bones media server for our house.  Thanks

---

