---
title: "problem installing testdisk"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by iispyderii on 2008-01-13
im trying to recover a lost partion that i accidentally formatted. i got news on the testdisk program but im having problems on how to install it by either terminal or manual

ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk

and i already tried the sudo apt-get update
i am running the ubuntu live cd, so it should still work right?

so can someone help me with installing this program and how to install general programs by manually downloading archived tar files.

---

### Post by oldos2er on 2008-01-13
You can't install packages while running the LiveCD. The best live CD for disk recovery is [http://distrowatch.com/systemrescue](http://distrowatch.com/systemrescue)

 To install programs on Ubuntu, see [https://help.ubuntu.com/7.10/add-applications/C/index.html](https://help.ubuntu.com/7.10/add-applications/C/index.html)

---

### Post by Rui Pais on 2008-01-13
> **iispyderii said:**
> im trying to recover a lost partion that i accidentally formatted. i got news on the testdisk program but im having problems on how to install it by either terminal or manual

ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk

and i already tried the sudo apt-get update
i am running the ubuntu live cd, so it should still work right?


Hi,
i have done this recently... and yes you can intsall programs on livecd.
Try open synaptic and on menus go Settings -> Repositories and check if 'universe' is enabled.
If not, enable it and do reload.hat should be enough.

> so can someone help me with installing this program and how to install general programs by manually downloading archived tar files.
Better, if you decide to install manually it's download ubuntu package from here:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=testdisk&searchon=names&subword=1&version=gutsy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=testdisk&searchon=names&subword=1&version=gutsy&release=all)
and install with sudo dpkg -i

---

