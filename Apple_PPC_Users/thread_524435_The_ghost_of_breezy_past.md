---
title: "The ghost of breezy past"
date: 2007-08-13
forum: Apple PPC Users
---

### Post by supremedalek on 2007-08-13
I installed ubuntu 5.10 in my Mac cube.  Then, I updated it to dapper (6.06) by editing the file /etc/apt/sources.list, changing "breezy" to "dapper," and then doing a "sudo apt-get dist-upgrade." That seemed to have taken place without issues.  But, it seems it is still somehow looking for 5.10:

raub@krab:~$ sudo apt-get update
Password:
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012) dapper
Release.gpg
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012) dapper
Release
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012)
dapper/main Packages
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012)
dapper/restricted Packages
Err cdrom://Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012)
dapper/main Packages

How come?

---

### Post by ssam on 2007-08-13
looks like you still have cdrom lines in you /etc/apt/source.list . if you have an internet connection then you don't need to be getting any packages from cd, so it is safe to take them out.

also remember that the proper way to do updates between distro versions is using update-manager. dist-upgrades are not officially supported

---

### Post by supremedalek on 2007-08-13
Here is my sources.list:

> raub@krab:~$ cat /etc/apt/sources.list
## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
raub@krab:~$ 

I searched and searched and cannot find any references to cdroms and breezy in it. So, I am feeling rather dumb right now...

About update-manager, can it be run command line or it is graphics-only?

---

### Post by ssam on 2007-08-14
maybe apt has got its package database messed up. it is stored in
```

/var/cache/apt

```

in mine i see pkgcache.bin and srcpkgcache.bin

then run apt-get update agin to recreate them.

---

