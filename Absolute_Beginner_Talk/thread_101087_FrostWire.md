---
title: "FrostWire"
date: 2005-12-09
forum: Absolute Beginner Talk
---

### Post by The Hedgehog on 2005-12-09
How do you install FrostWire?

---

### Post by amohanty on 2005-12-09
Looking at the website they distribute rpms and source.

To install from rpm use alien:
[http://ubuntuforums.org/showpost.php?p=510155&postcount=4](http://ubuntuforums.org/showpost.php?p=510155&postcount=4)

To install from source:
just do the same old:
```
./configure
make
sudo make install
```

routine. I would also suggest looking at checkinstall (universe repos). So instead of doing a 

```
sudo make install
```

you would do a

```
sudo checkinstall
```

This generates a .deb. file and installs it, so you can use dpkg with it.

HTH

---

### Post by codejunkie on 2005-12-09
[quote=The Hedgehog]How do you install FrostWire?[/quote] install sun java first download this FrostWire package [http://home.fuse.net/t3dcinc-887b/mirror/downloads/bin/FrostWire-4.9.37-0-Any-OS.zip]("http://home.fuse.net/t3dcinc-887b/mirror/downloads/bin/FrostWire-4.9.37-0-Any-OS.zip")
extract it, cd into that dir and run it with this ```
java -jar FrostWire.jar
```

---

### Post by amohanty on 2005-12-09
[QUOTE=codejunkie]install sun java first[/QUOTE]

The easiest way to do it is to use the plf repos, add the following to your /etc/apt/sources.list (REMEMBER to comment them out, after you are done - add # to the front of the line, so that other things dont get updated accidentally)

> deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free



Then just fire up synaptic and look for sun-jre

HTH

---

