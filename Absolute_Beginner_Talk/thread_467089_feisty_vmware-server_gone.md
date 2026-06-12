---
title: "feisty vmware-server gone?"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by muguwmp67 on 2007-06-07
I went to synaptic to install vmware-sever today and it is not in the repositories.  Is it no longer available for feisty?  All that is there is vmware-player, and from what I understand, I can't set up a new vm with that.

---

### Post by whizbaby on 2007-06-07
Dont know what repositories you have but when I type

apt-cache search vmware

vmware-server appears (im on feisty, too). So it must be you :P

---

### Post by muguwmp67 on 2007-06-07
All I see when I do the apt-cache is the vmware-server-modules:
```

$ apt-cache search vmware-server
vmware-server-kernel-modules-2.6.20-15 - vmware-server modules for Linux (kernel 2.6.20)
vmware-server-kernel-modules-2.6.20-16 - vmware-server modules for Linux (kernel 2.6.20)
vmware-server-kernel-modules - vmware-server kernel module dependency package

```

After sudo apt-get update
```

$ sudo apt-get install vmware-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vmware-server

```

These were there two weeks ago.  I did a sudo apt-get autoclean last weekend, but I do not know how this could have affected it.

---

### Post by whizbaby on 2007-06-07
xxx@yyy:~$ apt-cache search vmware-server
vmware-server-kernel-modules-2.6.20-15 - vmware-server modules for Linux (kernel 2.6.20)
vmware-server-kernel-modules - vmware-server kernel module dependency package
vmware-server-kernel-modules-2.6.20-16 - vmware-server modules for Linux (kernel 2.6.20)
vmware-server - Free virtual machine server from VMware
vmware-server-kernel-source - Kernel modules for VMware Server.
xxx@yyy:~$ 

how bout takin a look at your /etc/apt/sources.list?

---

### Post by peterbrewer on 2007-06-07
You need to add the canonical commercial repo to your sources list.  The address is:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

It is not added by default.  VMWare Server will now show up.

---

### Post by muguwmp67 on 2007-06-07
Thanks Peter, that did the trick

---

