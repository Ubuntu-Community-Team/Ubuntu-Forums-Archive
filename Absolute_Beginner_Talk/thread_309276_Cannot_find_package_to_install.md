---
title: "Cannot find package to install"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by minotaurjim on 2006-11-29
[https://help.ubuntu.com/community/Radeon%209200/9250%20(RV280)%20and%20DVI](https://help.ubuntu.com/community/Radeon%209200/9250%20(RV280)%20and%20DVI)

Following those instructions^ I try:
```
$ sudo apt-get build-dep xserver-xorg-driver-ati
```

and it says it can't find the packages.  I can do the apt-get updates one and it find and install any updates. But this one won't work.  Have they moved it and the documentation is old?

---

### Post by daniminas on 2006-11-29
Check in /etc/apt/sources.list if you have the repositories where is that driver..

---

### Post by nickburns on 2006-11-29
Go to System >> Administration >> Synaptic 

Then Settings >> Repositories

Check all the repositories and click OK

Then in the upper left corner hit the refresh button...

Then go back to the terminal and try to run what you want.

---

### Post by minotaurjim on 2006-11-29
```
jim@Ubuntu:~$ sudo apt-get install build-essential fakeroot
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
fakeroot is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 28 not upgraded.
jim@Ubuntu:~$ sudo apt-get build-dep xserver-xorg-driver-ati
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for xserver-xorg-driver-ati
jim@Ubuntu:~$ 

```

Nada. This is what it gives me.

any other suggestions?

---

### Post by nickburns on 2006-11-30
Looks like you may be able to download the package here.

[http://packages.ubuntulinux.org/dapper/x11/xserver-xorg-driver-ati](http://packages.ubuntulinux.org/dapper/x11/xserver-xorg-driver-ati)

---

