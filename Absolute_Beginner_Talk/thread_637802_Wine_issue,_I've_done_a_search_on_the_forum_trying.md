---
title: "Wine issue, I've done a search on the forum trying to solve."
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Rich Lee on 2007-12-11
*I'm just trying to install Wine at this point. I followed the instructions here [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) I tried to install using the Terminal and the add/remove programs area.*

sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libasound2 (> 1.0.14) but 1.0.10-2ubuntu4 is to be installed        Depends: libc6 (>= 2.6-1) but 2.3.6-0ubuntu20 is to be installed
        Depends: libgphoto2-2 (>= 2.4.0) but 2.1.6-5.2ubuntu8 is to be installed        Depends: libgphoto2-port0 (>= 2.4.0) but 2.1.6-5.2ubuntu8 is to be insta lled
        Depends: liblcms1 (>= 1.15-1) but 1.13-1 is to be installed
        Depends: libxml2 (>= 2.6.29) but 2.6.24.dfsg-1ubuntu1 is to be installed        Depends: libxslt1.1 (>= 1.1.20) but 1.1.15-1ubuntu1 is to be installedE: Broken packages
rich@rich-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 188 not upgraded.
rich@rich-desktop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.


I AM in the process of learning, but I'm very committed to doing so :-({|=
Any help, and/or just pointing to another relevant post would be appreciated.

---

### Post by HermanAB on 2007-12-11
In general, before installing something that is very complex like Wine, first update your system to make sure that you have the latest and greatest of everything.  Otherwise, you will get lost in dependency hell.

Cheers,

H.

---

### Post by Rich Lee on 2007-12-11
Thanks I'll try that, should I just hit update all in the add/remove programs area or use a Terminal command to do that?

I just downloaded Ubuntu a day or two ago.

---

### Post by PmDematagoda on 2007-12-11
Could you please post the result of:-
```

cat /etc/apt/sources.list
```

---

### Post by Rich Lee on 2007-12-11
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

Absolutely.

---

### Post by shafin on 2007-12-11
Go to System>Administration>Update Manager and install available upgrades.

---

### Post by shafin on 2007-12-11
> **Rich Lee said:**
> deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

Absolutely.
You have to add the winehq repository there.

---

### Post by Rich Lee on 2007-12-11
Okay giving that a try right now.

---

### Post by PmDematagoda on 2007-12-11
You can also use the normal repos.

Go to Software Sources in System>Administration>Software Sources.

Then enable all the repositories in the Ubuntu Software tab.

After that reload the sources list as requested and then do:-
```

sudo apt-get install -f
```

After that is completed you can try installing Wine again.

---

### Post by Rich Lee on 2007-12-11
Thanks "guys" I think I got it working now.:KS

---

