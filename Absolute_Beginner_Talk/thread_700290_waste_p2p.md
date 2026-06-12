---
title: "waste p2p"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Doorslammer on 2008-02-18
tried to install waste 
I got waste-linux-1.5-beta-3.zip from here:
[http://sourceforge.net/project/showf...kage_id=147272](http://sourceforge.net/project/showf...kage_id=147272)
then installed 
sudo apt-get install libwxgtk2.6-dev wx-common 

here is the error's I got 

```
~/wxwaste_1.5_beta_4/waste$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name...
configure: error: C++ compiler cannot create executables
See `config.log' for more details.

```

---

### Post by justleen on 2008-02-18
what dfid the config.log say?

and try running it as root? (should _NOT_ be neccesary for a configure!! but you never know..)

---

### Post by Doorslammer on 2008-02-18
as root got the same thing

---

### Post by Doorslammer on 2008-02-18
looks like I don't have g++ 
so I just installed that 
& everything is working now ll

---

