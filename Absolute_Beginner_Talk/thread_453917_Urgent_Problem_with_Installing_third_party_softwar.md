---
title: "Urgent Problem with Installing third party software"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by yuhikaru on 2007-05-24
Hi,

I am new to Ubuntu but so far I really like its interface and yes, even command line TERMINAL. However, the learning curve is a bit steep for me as I encounter many problems in executing installation of third party software such as Gnozip (similar to Winzip for Windows OS). I tried to follow the command line instructions faithfully but there are error messages which I cannot resolve.

upon the command: ./configure

I encounter the following error messages:

jude@Otagon:~/gnozip-0.1.3$ ./configure
loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.

I truly appreciate some form of help here. Without knowing how to install programs, my OS is almost as good as dead. Thank you~~in advance.

---

### Post by Seisen on 2007-05-24
You need to install build-essential. You can either search in Synaptic for "build-essential" or do this in the terminal

```
sudo apt-get install build-essential
```

---

