---
title: "beryl install problems"
date: 2007-06-07
forum: Apple PPC Users
---

### Post by athomenator on 2007-06-07
im new to ubuntu for ppc and i was wondering how to fix this problem
i was trying to install beryl on my computer and it doen't seem to work
this is waht i did

rick@rick-linux:~$ sudo -i
root@rick-linux:~# cd /
root@rick-linux:/# cd home
root@rick-linux:/home# cd rick
root@rick-linux:/home/rick# cd beryl
root@rick-linux:/home/rick/beryl# cd beryl-core-0.2.1
root@rick-linux:/home/rick/beryl/beryl-core-0.2.1# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
root@rick-linux:/home/rick/beryl/beryl-core-0.2.1# make
make: *** No targets specified and no makefile found.  Stop.
root@rick-linux:/home/rick/beryl/beryl-core-0.2.1# 

but i don't know hot to fix it

please help

many thanks rick

---

### Post by luckyd on 2007-06-07
Why don't you just
> sudo apt-get install beryl-core ?

---

