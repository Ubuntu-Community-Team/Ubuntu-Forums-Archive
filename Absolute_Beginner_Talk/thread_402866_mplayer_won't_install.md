---
title: "mplayer won't install?"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by miggols99 on 2007-04-06
I am trying to install Mplayer, but when I try to install it anywhere, it won't select or it won't install. When I try install with aptitude:
```
sudo aptitude install mplayer
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
No candidate version found for mplayer
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

```
All the repos are enabled...

---

### Post by taurus on 2007-04-06
Can you post your /etc/apt/sources.lisl?

```
cat /etc/apt/sources.list
```

---

### Post by miggols99 on 2007-04-06
```

deb http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted 
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted 
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ edgy universe 
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse 
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse 

deb http://security.ubuntu.com/ubuntu edgy-security main restricted 
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted 
deb http://security.ubuntu.com/ubuntu edgy-security universe 
deb-src http://security.ubuntu.com/ubuntu edgy-security universe 

## Swiftfox
deb http://getswiftfox.com/builds/debian unstable non-free 

## NTFS read/write
deb http://flomertens.free.fr/ubuntu/ edgy main main-all 
deb http://ntfs-3g.sitesweetsite.info/ubuntu/ edgy main main-all 
deb http://flomertens.keo.in/ubuntu/ edgy main main-all 
```

---

### Post by taurus on 2007-04-06
Try

```
sudo aptitude update
sudo aptitude install mplayer
```

---

### Post by miggols99 on 2007-04-06
No. The same error still appears. I think some packages are not there. Look at the screenshot.

---

### Post by shirilover on 2007-04-06
You need to either enable the multiverse repository(easy).
Just add multiverse to the end of the follwing:
```

deb http://gb.archive.ubuntu.com/ubuntu/ edgy universe 
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy universe 

```

However, I much prefer compiling MPlayer from SVN source(more difficult).

---

### Post by zvacet on 2007-04-06
Can you mark it for install in Adept?I belive you can find it in add/remove programs.In Adept is in multiverse reository.

---

### Post by miggols99 on 2007-04-06
It's still showing the same error message...

---

### Post by miggols99 on 2007-04-06
>   Can you mark it for install in Adept?I belive you can find it in add/remove programs.
Actually no. When I press 'request install' it does nothing. When I use add/remove programs, it does the same.

---

### Post by zvacet on 2007-04-06
Download binary package from their site.

Edit:Forget about this.

---

### Post by miggols99 on 2007-04-06
Looks like they don't supply Debian/Ubuntu packages. I don't want to compile from source.

---

