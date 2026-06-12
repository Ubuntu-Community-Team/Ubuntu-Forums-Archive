---
title: "problems wirh apt"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by ojasvi rajpal on 2006-10-20
Hi, I am having a particular difficulty with apt . whenever I try to install new pacakges by commands like "$ sudo apt-get install xmms" . it shows the following message which is expected:

" Reading package lists... Done
Building dependency tree... Done
Recommended packages:
  libmikmod2
The following NEW packages will be installed:
  xmms
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1054kB of archives.
After unpacking 7430kB of additional disk space will be used.
"
but when I type yes it gives the following message 

"Media change: please insert the disc labeled
 'Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531.2)'
in the drive '/cdrom/' and press enter
"
. It happens for some packages and not for others ( I ionstalled wine easily with apt and many more things ) . As i don't have the dvd with me now its a trouble can anybody help ??

2.) I installed a 3d-chess game via  synaptic it is installed ( as shown by synaptic ) but i can't find it . plz help ??

---

### Post by taurus on 2006-10-20
Either insert the CD into the drive or remove the line in /etc/apt/sources.list that has your CD in it, usually the first line or near the top!!!

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by ojasvi rajpal on 2006-10-20
Thanks can u plz solve the second problem too

---

### Post by Kateikyoushi on 2006-10-20
In synaptic right click the package select properties and in the installed files tab you can see where are the package related files.

---

