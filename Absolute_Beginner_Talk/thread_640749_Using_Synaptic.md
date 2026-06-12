---
title: "Using Synaptic"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by gil michael on 2007-12-14
Hi,
Almost everything i try to download using synaptic ends up with an error, or the download doesn't start at all.
I tried to add the Universe, Multiverse and Restricted repositories, i'm unable to download them as well.
What can be the problem?

Regards,
Gil

---

### Post by spiderbatdad on 2007-12-14
can you post  /etc/apt/sources.list?

---

### Post by wpshooter on 2007-12-14
What version of Ubuntu are you using ?

---

### Post by thelatinist on 2007-12-14
Could you also please post the error messages you are receiving? Typically such error messages are essential to troubleshooting the problem causing them.

---

### Post by gil michael on 2007-12-14
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main multiverse restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by gil michael on 2007-12-14
For example, this is what i get when i try to install Universe, Multiverse and Restricted repositories... It stays on 7 out of 21 files for a long time (30 minutes)[ATTACH]53236[/ATTACH]

---

### Post by spiderbatdad on 2007-12-14
```
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://il.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://il.archive.ubuntu.com/ubuntu/ edgy universe

``` shows those repos are not enabled...you can fix by uncommenting the last two lines, but as was suggested, the error msg is important, and the method you are trying to use to install the software.

---

### Post by gil michael on 2007-12-14
Or this error:



W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.22-1ubuntu4.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.22-1ubuntu4.4_i386.deb)
  Connection failed


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.22-1ubuntu4.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.22-1ubuntu4.4_i386.deb)
  Connection failed


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.22-1ubuntu4.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.22-1ubuntu4.4_i386.deb)
  Connection failed

---

