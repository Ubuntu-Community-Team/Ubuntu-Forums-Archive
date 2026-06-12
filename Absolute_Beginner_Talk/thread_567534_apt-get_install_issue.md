---
title: "apt-get install issue"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by bigjoe7 on 2007-10-04
how do i get past this issue?

root@White-Dragon:~# apt-get install snort postgresql-8.1 snort-pgsql
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package snort

---

### Post by Jussi Kukkonen on 2007-10-04
Enable universe repository: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by bigjoe7 on 2007-10-05
Hi,

I originally performed that action.

from /etc/apt/sources.list

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

then performed a apt-get upgrade.

root@Black-Dragon:~# apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [50.9kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release [50.9kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [124kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Sources
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [7830B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [24.8kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [979B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [74.3kB]
Get:11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages [145kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [9690B]
Get:13 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Sources [50.5kB]
Get:15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Fetched 540kB in 0s (663kB/s)
Reading package lists... Done

Still get the error message.

Is there anything else that needs to performed?

---

### Post by RomeReactor on 2007-10-05
Hi. You're only enabling the security repositories for Universe; please post your full sources.list:
```
cat /etc/apt/sources.list
```

Alternatively, open Synaptic and go to "Settings->Repositories" and on the tab for "Ubuntu Software", make sure all the repositories are checked. In case Dapper's Synaptic doesn't offer you that functionality, go to "System->Administration->Software Sources" and enable all the repositories there.

If Dapper doesn't have that either, then you'll have to enable them by hand in Gedit.

---

### Post by bigjoe7 on 2007-10-05
Hi

Im not running X windows, so its all done by the shell

here is the cat output.

excaliber@White-Dragon:~$ more /etc/apt/sources.list
#
deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted


deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
excaliber@White-Dragon:~$

---

### Post by RomeReactor on 2007-10-05
That's odd; you should be able to get it. Maybe try an apt-get update?

In any case, here's a direct link to Dapper's [snort from a UK mirror]("http://ubuntu.blueyonder.co.uk/archive/pool/universe/s/snort/snort_2.3.3-5ubuntu2_i386.deb"). Try downloading that, install it with dpkg, and let Ubuntu sort out the dependencies.

---

