---
title: "Wifi Help"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by xXx 0wn3d xXx on 2006-03-26
I have a Broadcom wifi card and I'm following a tutorial and it says I need the drivers. Where can I find them ?

---

### Post by Papa-san on 2006-03-26
It's going to depend on which card you have.
The tutorial in wiki on 'ndiswrapper' has a link to driver sources. As well as a lot of other vital info for us nOObs!
Patience... It took me three weeks to get mine going, but it works now!
[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper)

---

### Post by xXx 0wn3d xXx on 2006-03-26
[QUOTE=Papa-san]It's going to depend on which card you have.
The tutorial in wiki on 'ndiswrapper' has a link to driver sources. As well as a lot of other vital info for us nOObs!
Patience... It took me three weeks to get mine going, but it works now!
[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper)[/QUOTE]
how can I find out what model I have ? I tried lspci but I get Broadcom 44808 ( Something like that) Unknown Device.

---

### Post by mdmarmer on 2006-03-26
You can use the windows drivers 
Copy all of them (.inf, .sys and maybe also .cat) to a directory in linux
and use ndiswrapper

The only problem with this approach is if you want 64-bit drivers and you don't have 64-bit Windows drivers

Mike

---

### Post by rhthekida on 2006-03-26
I have a Linksys card that is supported by ndiswrapper, I have already checked, but I am unable to install ndiswrapper-utils or ndisgtk. I think It may have something to do with my repositories any help?


# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://ftp.au.debian.org/debian](http://ftp.au.debian.org/debian) unstable main contrib non-free
deb-src [http://ftp.au.debian.org/debian](http://ftp.au.debian.org/debian) unstable main contrib non-free

---

### Post by xXx 0wn3d xXx on 2006-03-26
Try insatlling tem using synaptic, Also try using [ this ](http://ubuntuforums.org/showthread.php?t=87946&highlight=recommended+sources.list) sources.list.

---

### Post by rhthekida on 2006-03-26
thanks a lot, that fixed a lot of problems I was having. Now I have ndiswrapper installed and am trying to use it on the .inf file in the driver i downloaded and extracted from the ndiswrapper compatability site. There are two .inf files in the extracted files, lsbcmnds.inf and AUTORUN.INF. I have tried to put both of those into ndiswrapper but when I <ndiswrapper -l> it says both are invalid drivers. Any ideas or help?

---

