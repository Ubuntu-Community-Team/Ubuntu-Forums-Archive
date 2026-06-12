---
title: "NETGEAR w111 v3 on ubuntu 7.10"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by simocusi on 2007-11-29
I have seen some threads on this subject but no one is clear to me.
I have just installed ubuntu 7.10 and therefore have no internet connection.
When I do the first command most of the people say (ndiswrapper -i netwg111.inf) it returns no diswrapper utils found. 

Can anyone please tell me step by step the commands I have to type? 

Thanks a lot!!

---

### Post by RomeReactor on 2007-11-29
Hi. You'll need to download [ndiswrapper-common]("http://mirrors.xmission.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.43-1ubuntu2_all.deb") and [ndiswrapper-utils]("http://mirrors.xmission.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb") on another computer (or if you dual boot, from your other OS); then transfer the packages to Ubuntu via USB drive or a CD, and  double click on each to install them. Then run the ndiswrapper command again.

Welcome to the community!

---

