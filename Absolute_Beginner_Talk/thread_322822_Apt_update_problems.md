---
title: "Apt update problems"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by AlexHT on 2006-12-21
Using ubuntu 6.06 LTS

I have a problem with apt-get and not able to upgrade at all. All i'm getting is a list of errors and failure to connect/fetch from various websites. I am connected to the internet and can browse websites freely. Please help.

---

### Post by riven0 on 2006-12-21
> **AlexHT said:**
> Using ubuntu 6.06 LTS

I have a problem with apt-get and not able to upgrade at all. All i'm getting is a list of errors and failure to connect/fetch from various websites. I am connected to the internet and can browse websites freely. Please help.

It'll probably be better to post the error message so we can see where the problem is.

---

### Post by AlexHT on 2006-12-21
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Connection failed [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Connection failed [IP: 146.137.96.15 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Connection failed [IP: 195.248.90.38 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Connection failed
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:) Connection failed
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:) Connection failed [IP: 146.137.96.15 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:) Connection failed
[http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.38 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:) Connection failed [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:) Connection failed [IP: 146.137.96.15 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:) Connection failed
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.38 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.15 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:) Connection failed
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.15 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.38 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:) Connection failed [IP: 146.137.96.15 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:) Connection failed
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:) Connection failed [IP: 146.137.96.15 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz:) Connection failed

This happens when i go to System > Administration > Update Manager

---

### Post by NeoLithium on 2006-12-21
Can you copy and paste the output of this, from a terminal window?
```
cat /etc/apt/sources.list
```

---

### Post by AlexHT on 2006-12-21
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by NeoLithium on 2006-12-21
Aha, try replacing this line:
```
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
``` with this line: ```
#deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
```
See if that does the trick?

---

### Post by AlexHT on 2006-12-21
I added the # and then did "apt-get update"

and i got this

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 146.137.96.7 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed [IP: 146.137.96.7 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
  Connection failed [IP: 146.137.96.7 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
  Connection failed [IP: 146.137.96.7 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
  Connection failed [IP: 146.137.96.7 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
  Connection failed [IP: 146.137.96.7 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
  Connection failed [IP: 146.137.96.7 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 195.248.90.38 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
  Connection failed [IP: 195.248.90.38 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  Connection failed [IP: 195.248.90.38 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 195.248.90.38 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Connection failed [IP: 146.137.96.7 80]Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Connection failed [IP: 195.248.90.38 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz)  Connection failedFailed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.38 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.38 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.38 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by riven0 on 2006-12-21
> **AlexHT said:**
> deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

I don't know, but that **deb cdrom** line just doesn't look right. Try commenting that out and do a sudo apt-get update again. See what happens.

EDIT: Oops, sorry, I see you already did that. Looks like it's time for bed for me.

---

### Post by NeoLithium on 2006-12-21
I found the problem. right after the uncommented CDROM line, add this:
```
 deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
```

Fixed, it should look like this, before you want to change any repositories.

```
 
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

---

### Post by AlexHT on 2006-12-21
cat /etc/apt/sources.list
```

# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```

I added the line but i'm still getting the same errors.
Oh, I'm also behind a router. Would that cause these errors?

---

### Post by NeoLithium on 2006-12-21
Yeah; that very well could be, I was hoping it was the sources list as I'm not familiar with a setup for the router, since I don't have one myself.  I fly around a few help files and see if I don't find something that could be of use to you.

---

### Post by NeoLithium on 2006-12-21
[http://ubuntuforums.org/showthread.php?p=1850096#post1850096](http://ubuntuforums.org/showthread.php?p=1850096#post1850096)

This might offer some help; they were able to use the internet; but not use aptitude to update their linux boxes. :)  Hope this points you in the right direction.

---

### Post by AlexHT on 2006-12-21
Thank you very much for spending the time to help me out. I will go through that tomorrow in hopes of finding an answer but I must head to bed now.

---

### Post by pandu.rs on 2006-12-21
I have already experienced the same problem. 
I removed the following line from /etc/apt/apt.conf

Acquire::http::Proxy "false";

and then it worked fine. hope this helps

---

### Post by shilliard on 2007-01-03
Thanks pandu.rs, that solved it for me too

---

