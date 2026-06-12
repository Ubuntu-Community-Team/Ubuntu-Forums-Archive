---
title: "Install package without network"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by djhworld on 2006-08-15
Hi there.

I'm attempting to get my wireless usb adapter working. But first I need ndiswrapper-utils - right? Well seeing as I have no Internet connection on Ubuntu I can't exactly just go to Synaptic Package Manager and download/install it. 

So, as I type this from my Windows partition, is there anyway of downloading the package from (somewhere?) and being able to install it without the network? 

Do I put it in some folder or something and just use apt-get?

---

### Post by tonym on 2006-08-15
Download the package from [http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils_1.8-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils_1.8-0ubuntu2_i386.deb)

Install it by dpkg -i ndiswrapper-utils_1.8-0ubuntu2_i386.deb

Regards

Tony.

---

### Post by djhworld on 2006-08-15
Excellent, thanks, will go and try it now.

---

