---
title: "mol-drivers-macosx missing"
date: 2005-03-12
forum: Apple PPC Users
---

### Post by Leonida on 2005-03-12
I've followed [MacOnLinuxHowto](http://www.ubuntulinux.org/wiki/MacOnLinuxHowto/) instructions, building and installing the mol modules with succes:
```
bash:~$ sudo dpkg -i /usr/src/mol-modules-2.6.10-4-powerpc_0.9.70+ubuntu0_powerpc.deb
```
But when i try to install the rest of the Mac-on-Linux packages mol-drivers-macos and mol-drivers-macosx are not find:
```
bash:~$ sudo apt-get install mol mol-drivers-linux mol-drivers-macos mol-drivers-macosx
Password:
Reading Package Lists... Done
Building Dependency Tree... Done
mol is already the newest version.
mol-drivers-linux is already the newest version.
E: Couldn't find package mol-drivers-macos
```
And after molvconfig, when I try to start mol I get this:
```
bash:~$ startmol -X
Mac-on-Linux 0.9.70 [Jan 24 2005 20:08]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 1
Loading Mac-on-Linux kernel module:
FATAL: Module mol not found.
====================================================================
  Failed to load the Mac-on-Linux kernel module -- please install
  mol-modules-source and build your own, or find a binary package
  providing mol-modules for your running kernel.
====================================================================
```

```
bash:~$ sudo startmol --list
Password:
--------------------------------------------------------------
  Running kernel:         2.6.10-4-powerpc
--------------------------------------------------------------
  Available modules:
    <none>
--------------------------------------------------------------
``` 

Thanks, .L.
--------------------------------------------------
iBook G4 933Mhz
Ubuntu 5.04 Hoary Hedgehog
MacOSX 10.3.8
mol 0.9.70-16ubuntu1

---

### Post by farruinn on 2005-03-12
Double check that multiverse is enabled becuase both mol-drivers-macos and mol-drivers-macosx are in multiverse.  As for mol not being able to find the module, I get the same thing with the same exact versions of what you have though.

---

### Post by Leonida on 2005-03-12
[QUOTE=farruinn]Double check that multiverse is enabled becuase both mol-drivers-macos and mol-drivers-macosx are in multiverse.  As for mol not being able to find the module, I get the same thing with the same exact versions of what you have though.[/QUOTE]
Thanks, I've found mol-drivers-macosx adding:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

as my /etc/apt/sources.list has not hoary multiverse.

Now it work  :-D

---

### Post by farruinn on 2005-03-12
So now startmol -X works for you?  It certainly isn't working here...

---

### Post by Leonida on 2005-03-12
[QUOTE=farruinn]So now startmol -X works for you?  It certainly isn't working here...[/QUOTE]
 :sad: I whish help you :sad:
Here some screenshots:
[http://www.freesmug.org/Members/Gand/img/mol01.png/](http://www.freesmug.org/Members/Gand/img/mol01.png/) - QuickTime
[http://www.freesmug.org/Members/Gand/img/mol02.png/](http://www.freesmug.org/Members/Gand/img/mol02.png/) - Shira browser
[http://www.freesmug.org/Members/Gand/img/mol03.png/](http://www.freesmug.org/Members/Gand/img/mol03.png/) - Firefox running flash
[http://www.freesmug.org/Members/Gand/img/mol04.png/](http://www.freesmug.org/Members/Gand/img/mol04.png/) - Exposé
[http://www.freesmug.org/Members/Gand/img/mol05.png/](http://www.freesmug.org/Members/Gand/img/mol05.png/) - Genie effect

It work fine with browser (Firefox, Camino,Shira, Safari, also with flash) but iTunes or QuickTime send my cpu over 100%

---

### Post by farruinn on 2005-03-15
My stupid mistake: the kernel I was running wasn't the most recent kernel.  I've since rebooted and it works.

---

### Post by Leonida on 2005-03-17
[QUOTE=farruinn]My stupid mistake: the kernel I was running wasn't the most recent kernel.  I've since rebooted and it works.[/QUOTE]:grin: :grin: 


Here are all my screnshots:
[http://www.freesmug.org/forums/foss.nbs/275805139923](http://www.freesmug.org/forums/foss.nbs/275805139923)

---

