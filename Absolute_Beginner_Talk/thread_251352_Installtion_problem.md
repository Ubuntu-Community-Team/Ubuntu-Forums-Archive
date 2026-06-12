---
title: "Installtion problem"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by debasishg on 2006-09-05
When i trying to install squid in my ubuntu 5.10, its showing the follwoing error....
```
debasish@ubuntu:~/Desktop/squid-2.5.STABLE6$ ./configure
loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for mawk... mawk
checking whether make sets ${MAKE}... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking whether the C compiler (gcc  -g) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.

```

why should i do? please help.

---

### Post by monktbd on 2006-09-05
you will need 

> sudo apt-get install build-essential

not sure this package already existed on breezy.

---

### Post by taurus on 2006-09-05
```

sudo aptitude update
sudo aptitude install build-essential

```
Then, run ./configure again...

---

