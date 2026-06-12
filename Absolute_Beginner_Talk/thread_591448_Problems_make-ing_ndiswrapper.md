---
title: "Problems make-ing ndiswrapper"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by chimerical_brio on 2007-10-25
So...I'm having trouble installing ndiswrapper. I did a complete reinstall of Ubuntu rather than just upgrading from Feisty to Gutsy. I can't remember whether make was already installed or if I installed build-essentials from the CD; regardless, make is on my machine. Downloaded ndiswrapper-1.48, ran make distclean, then tried running make. When I run make, I get a long error regarding the /utils directory, with lots of files not existing. When it finally fails, I'm told that it encountered "Error 2." Any ideas? I can transfer files over using a USB drive, but I dont' have access to the internet on that computer (hence needing ndiswrapper). Many thanks.

---

### Post by chimerical_brio on 2007-10-25
Anyone?

---

### Post by chimerical_brio on 2007-10-25
I'm sorry to keep doing this, but...bump.

---

### Post by MegaJim on 2007-10-25
Can you try installing ndiswrapper from the distribution CD you used ?

---

### Post by Daveth on 2007-10-25
this may be relevant:

" Installation

Ubuntu comes with the necessary ndiswrapper module pre-installed, but it needs the ndiswrapper-utils package to get it working. There is also a graphical interface to using ndiswrapper which you can use. 

NOTE: in Edgy, you must install the ndiswrapper-utils-1.8 package instead of just ndiswrapper-utils. and then proceed with installation using the command ndiswrapper-1.8 instead of ndiswrapper. See  [https://launchpad.net/distros/ubuntu/+source/ndiswrapper/+bug/59983](https://launchpad.net/distros/ubuntu/+source/ndiswrapper/+bug/59983) for bug report. and  [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper/edgy](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper/edgy) for help installing. Note: for Ubuntu 6.06 (Dapper), ndiswrapper-utils is included on the standard installation CD. You can install the package from the CD and skip to section 2.2..."

from

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

