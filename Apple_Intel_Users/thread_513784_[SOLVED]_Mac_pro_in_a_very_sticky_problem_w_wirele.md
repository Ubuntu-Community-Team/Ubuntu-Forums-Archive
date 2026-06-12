---
title: "[SOLVED] Mac pro in a very sticky problem w/ wireless (7.04)"
date: 2007-07-30
forum: Apple Intel Users
---

### Post by macaholic on 2007-07-30
Ok, i have a mac pro with an airport extreme card. My problem is that I have NO way to get on the internet w/o wireless, it is either that or I run about 200 feet of cable. I read somewhere that newer versions of the feisty kernel support the airport card. (maybe?) I have other computers I can use for file transfer from one to the other, but I don't know what to download and what to do. Is there a way to manually update ubuntu (if it is indeed true that newer versions support my card) by downloading the update to another computer and then updating it manually?  Is there some other way to get it to work with just a clean install? Or am I completely screwed. Any help on this matter would be greatly appreciated.

---

### Post by PaulFr on 2007-07-31
1. **[https://wiki.ubuntu.com/PowerPCFAQ#head-9b97f90e99a0544334fbb98bdbbdb176ecb96444](https://wiki.ubuntu.com/PowerPCFAQ#head-9b97f90e99a0544334fbb98bdbbdb176ecb96444)** for Feisty support for Airport Extreme.

2. I presume you have Ubuntu on your other machine - if so, you can use ```
sudo apt-get install -d <package_name>
``` to download the <package_name>-<version_number>.deb package file for any package that you need. These package files will be placed in the **/var/cache/apt/archives** directory. You can copy these over to your Mac using disk/CD/stick/whatever and then install these .deb files using ```
sudo dpkg -i <name1>.deb <name2>.deb ...
```Hope this helps.

---

### Post by cyberdork33 on 2007-07-31
your wireless card is a broadcom-based wifi card. there are two ways to get these type of cards working bcm43xx or ndiswrapper. Pretty much any information about either method should work for you. Good luck.

---

### Post by macaholic on 2007-07-31
> **PaulFr said:**
> 1. **[https://wiki.ubuntu.com/PowerPCFAQ#head-9b97f90e99a0544334fbb98bdbbdb176ecb96444](https://wiki.ubuntu.com/PowerPCFAQ#head-9b97f90e99a0544334fbb98bdbbdb176ecb96444)** for Feisty support for Airport Extreme.

2. I presume you have Ubuntu on your other machine - if so, you can use ```
sudo apt-get install -d <package_name>
``` to download the <package_name>-<version_number>.deb package file for any package that you need. These package files will be placed in the **/var/cache/apt/archives** directory. You can copy these over to your Mac using disk/CD/stick/whatever and then install these .deb files using ```
sudo dpkg -i <name1>.deb <name2>.deb ...
```Hope this helps.

Thx I am going to try this now.:)

---

### Post by macaholic on 2007-07-31
I have tried a bunch of ways including downloading it via synaptic and it says it installs and extracts the firmware and it doesn't work. Am I missing a step? Does anyone know how to do it with an Airport Extreme, or even better has gotten an Airport extreme to work in Ubuntu 7.04 Feisty Fawn. I know have internet via ethernet on the computer that needs the serious help. If I don't get this to work I am not going to be able to use linux, so I NEED this to work somehow. And btw the instuctions at [https://wiki.ubuntu.com/PowerPCFAQ#head-9b97f90e99a0544334fbb98bdbbdb176ecb96444](https://wiki.ubuntu.com/PowerPCFAQ#head-9b97f90e99a0544334fbb98bdbbdb176ecb96444) 
Ya right, only two steps and it is supposed to magically work? HAH But nevertheless I tried it anyway and it still doesen't work.

---

### Post by cyberdork33 on 2007-07-31
you can't just specify airport extreme. Apple uses different chips in their wifi cards. Do lspci at the commandline to determine which you have.

For Broadcom, I suggest using ndiswrapper. It has always worked better for me. you need the windows driver to get that working though.

Read through this, it will tell you all your options.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by macaholic on 2007-07-31
It is a Broadcom 4328 btw. I am going to try ndiswrapper now.

---

### Post by macaholic on 2007-07-31
Solved it using ndiswrapper from a tutorial here, works with most newer imacs also.
[http://www.penlug.org/twiki/bin/view/Main/LinuxHardwareInfoAppleiMac24](http://www.penlug.org/twiki/bin/view/Main/LinuxHardwareInfoAppleiMac24)
Scroll down to wireless.

---

