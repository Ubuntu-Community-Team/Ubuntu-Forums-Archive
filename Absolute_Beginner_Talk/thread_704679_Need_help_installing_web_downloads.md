---
title: "Need help installing web downloads"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by i$leepy1 on 2008-02-22
Someone help me!!!  I am using ubuntu 7.10 and am very new to Linux.  How are web downloads installed that use the .tgz extension.  I am trying to install an Intel pro/wireless 2100 driver, ipw2100_linux_1_2_0.tgz.

Your help is greatly appreciated.

---

### Post by Cypher on 2008-02-22
First extract the contents of the tarball with
```

tar -zxvf ipw2100_linux_1_2_09.tgz

```
Now look at the README or INSTALL or whatever is there telling you what to do. If the driver is Kernel driver..then you'd probably have to copy it to /lib/modules/<kernel version> and load it using /etc/modules.conf

---

### Post by cozmicharlie on 2008-02-22
This will help explain:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by maduranga on 2008-02-22
if you want to install a specific software, check if it is available on ubuntu repositories. System > Administration > Synaptic package manager. it is the most easiest way to install package. hope that will help you

---

### Post by louieb on 2008-02-22
You may just have to go to system>adminstration>Network.
I just got a [Intel PRO/Wireless LAN 2100 3B Mini PCI adapter]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-59438") on EBay and it worked out of the box on my IBM T30 laptop.  It showed up as eth2 I just enabled roaming mode,  selected a network and it connected. 

:lolflag:  I had to use Ubuntu  to download the windows driver before it would work in XP.

---

