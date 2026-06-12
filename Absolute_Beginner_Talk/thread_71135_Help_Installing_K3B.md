---
title: "Help Installing K3B"
date: 2005-10-02
forum: Absolute Beginner Talk
---

### Post by BdON003 on 2005-10-02
Hi everyone, I am new here and also new to linux.  I am trying to install k3b, and I get  
"k3blibs:
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu14 is to be installed
  Depends: libfontconfig1 (>=2.3.0) but 2.2.3-4ubuntu7 is to be installed
  Depends: libidn11 (>=0.5.13) but 0.5.2-3 is to be installed
  Depends: libqt3c102-mt (>=3:3.3.4) but 3:3.3.3-7ubuntu3 is to be installed
  Depends: libvorbis0a (>=1.1.0) but 1.0.1-1 is to be installed
  Depends: libvorbisenc2 (>=1.1.0) but 1.0.1-1 is to be installed
  Depends: libvorbisfile3 (>=1.1.0) but 1.0.1-1 is to be installed"
when I try to install the k3blibs from the synaptic package manager.  I get a similar error message when I try to install k3b.  Any help?  I have the universe repository added

---

### Post by poofyhairguy on 2005-10-02
[QUOTE=BdON003]Hi everyone, I am new here and also new to linux.  I am trying to install k3b, and I get  
"k3blibs:
Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu14 is to be installed
Depends: libfontconfig1 (>=2.3.0) but 2.2.3-4ubuntu7 is to be installed
Depends: libidn11 (>=0.5.13) but 0.5.2-3 is to be installed
Depends: libqt3c102-mt (>=3:3.3.4) but 3:3.3.3-7ubuntu3 is to be installed
Depends: libvorbis0a (>=1.1.0) but 1.0.1-1 is to be installed
Depends: libvorbisenc2 (>=1.1.0) but 1.0.1-1 is to be installed
Depends: libvorbisfile3 (>=1.1.0) but 1.0.1-1 is to be installed"
when I try to install the k3blibs from the synaptic package manager.  I get a similar error message when I try to install k3b.  Any help?  I have the universe repository added[/QUOTE]

type in this command:

> sudo apt-get update

then try again!

---

