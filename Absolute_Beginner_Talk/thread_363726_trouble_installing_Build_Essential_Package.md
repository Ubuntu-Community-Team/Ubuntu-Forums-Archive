---
title: "trouble installing Build Essential Package"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by Jamesbowden on 2007-02-17
I have recently re-installed ubuntu and i have been setting it up the way i like it, however today i started to some C++ coding and when it was time to compile i realized that i did not that build-essential installed. however when i tried to install it via apt-get with

    ```
sudo apt-get install build-essential
```

i get 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnl1-pre6 network-manager libnm-util0 dhcdbd libxcomposite1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libstdc++6-4.1-dev
Suggested packages:
  debian-keyring gcc-4.1-doc lib64stdc++6 libstdc++6-4.1-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libstdc++6-4.1-dev
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4310kB of archives.
After unpacking 17.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)'
in the drive '/cdrom/' and press enter

```

i basically get the same when i try to install via synaptic. it just says

>  please insert the disc labeled
 'Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)'
in the drive '/cdrom/'

This has never happened to me before usually it just downloads the packages and installs them.

I don't have my Ubuntu CD with me so i cant use it.

does anyone know what the problem is?

---

### Post by taurus on 2007-02-17
You need to comment out the line in /etc/apt/sources.list regarding the CDROM so it won't ask you for it anymore.  Open a terminal and type

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the line that has CDROM in it (usually the first line).  Save it and run

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by Jamesbowden on 2007-02-17
Thanks that seems to have worked, its very strange that has never happened to me before, any idea why it did?

---

