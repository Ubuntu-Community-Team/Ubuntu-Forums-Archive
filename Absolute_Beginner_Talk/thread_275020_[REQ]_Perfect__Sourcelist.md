---
title: "[REQ] Perfect  Sourcelist"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by andril on 2006-10-10
I am a semi-noob to Linux and love this Ubuntu distro. I am currently running version 6.06 LTS (4th reinstall) and would like to start off the correct way this time. I am looking for the Perfect Source List - can you guys/gals help? ](*,) 

I would like one with these sources added:
Automatix
Beryl

AMD Athlon 2.0Ghz
1GB of DDR Ramm
Nvidia FX 5500 - 128mb

Thanks In Advance

---

### Post by aktiwers on 2006-10-10
Here is mine. It has Beryl, automatix and I dont know what you mean with those hardware specs..  but I have an 

AMD athlon XP 2800+ 
1gb ram
ATI Radeon 9800 pro ( there is nothing in my sourcelist about this)
> 
# The rest of your sources.list follows

#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx

---

### Post by jd65pl on 2006-10-10
You should have a look a [source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")!!!!

---

