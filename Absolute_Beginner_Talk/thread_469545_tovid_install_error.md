---
title: "tovid install error"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-06-10
Following instructions at: [http://ubuntuforums.org/showthread.php?t=183936&highlight=tovid]("http://ubuntuforums.org/showthread.php?t=183936&highlight=tovid")
which leads to
[http://tovid.wikia.com/wiki/Installing_tovid]("http://tovid.wikia.com/wiki/Installing_tovid")

Configuring seems to go ok, when I get to $ su -c "make install", i recieve 

```
ed@ed-desktop:~/tovid/tovid-0.30$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for txt2tags... :
checking for a Python interpreter with version >= 2.3... python
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/tovid-init
configure:

 You may now type 'su -c "make install"' to compile and install tovid.
 
ed@ed-desktop:~/tovid/tovid-0.30$ su -c "make install"
Password: 
su: Authentication failure
Sorry.

```

---

### Post by taurus on 2007-06-10
Try

```
sudo make install
```

---

### Post by jiminycricket on 2007-06-10
can you try "sudo make install" instead?

or do 'sudo aptitude install checkinstall && sudo checkinstall" instead, so you can uninstall it in Synaptic.

---

