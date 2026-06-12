---
title: "c compiler???"
date: 2005-06-02
forum: Absolute Beginner Talk
---

### Post by benevolent on 2005-06-02
Hello! I've downloaded the xmms player and try to install it. When i tried to "configure" it (./configure) there seemed to be an error with the way of installation and especially "configure: error: no acceptable C compiler found in path". So, i download a c compiler (gcc-2.95_2.95.4-22_i386.dep). i used the root terminal to install it and i used the command "sudo dpkg -i <name>.dep" and there was another error. 

"...
 dpkg:dependency problems prevent configuration at gcc2.95
 gcc-2.95 depends on cpp-2.95(>=1:2.95:4);however
 package cpp-2.95 is not install
 gcc-2.95 depends on coo-2.95(<<1:2.95:4);however
 package cpp-2.95 is not install
 ..."

what can i do? Should i download sth else before? Keep in mind that i haven't internet conection at ubuntu (yet..). Whatever i download, i download from windows ( :-\" ) and then i transfer the file...


thx!

---

### Post by Gustav on 2005-06-02
Find a newer version of gcc (the current stable one is 4.0)

if you search for it at packages.ubuntu.com you'll find what packages the package depends on.

---

### Post by felipe on 2005-06-02
hi, do you really want to compile the sources? i guess you should download the ubuntu package for xmms, instead. do this:

```

sudo apt-get install xmms -s

```

the -s switch just simulates the actual download and install and it does nothing, but it tells you if it needs to get additional packages in order to install xmms, so take the output of the above command, reboot windos and get those package(s), you can get them from here:

```

http://archive.ubuntu.com/ubuntu/pool/main/x/xmms/

```

and of course you can go up to look for other deb's. once you're back in ubuntu go to the dir where you stored the downloaded package(s) and do this:

```

sudo dpkg -i *.deb

```

make sure you don't have any other deb's in that dir, just those needed by xmms and xmms itself

have fun

---

### Post by az on 2005-06-02
[http://test.wiki.ubuntu.com/forum/software/Compiler](http://test.wiki.ubuntu.com/forum/software/Compiler)

The compiler is on your cd.

Why not use the precompiled version?  It is in universe.

---

### Post by somuchfortheafter on 2005-06-02
also the easiest way for you to install software is through synaptic, to find it go to system , administration, then select synaptic, through this program you can search and install any program in the ubuntu repositories.

---

