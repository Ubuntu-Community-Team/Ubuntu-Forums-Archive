---
title: "Server upgraded from ubuntu from 8.04 to Ubuntu 9.04 issue in apt-get"
date: 2011-01-30
forum: Apple Hardware Users
---

### Post by aliahsan81 on 2011-01-30
Hi All

My server is upgraded from ubuntu 8.04 to ubuntu 9.04 after that apt-get not working i have tried apt-get -f install apt-get update below is the error 

```

root@mail:/etc/apt# apt-get update
Hit http://archive.ubuntu.com jaunty Release.gpg
Hit http://archive.ubuntu.com jaunty-updates Release.gpg
Hit http://security.ubuntu.com jaunty-security Release.gpg
Hit http://ports.ubuntu.com jaunty Release.gpg 
Hit http://archive.ubuntu.com jaunty Release                         
Hit http://security.ubuntu.com jaunty-security Release               
Hit http://archive.ubuntu.com jaunty-updates Release                
Hit http://security.ubuntu.com jaunty-security/main Sources                               
Hit http://archive.ubuntu.com jaunty/main Sources                    
Hit http://archive.ubuntu.com jaunty/restricted Sources
Hit http://archive.ubuntu.com jaunty/universe Sources
Hit http://archive.ubuntu.com jaunty/multiverse Sources              
Hit http://security.ubuntu.com jaunty-security/restricted Sources    
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Hit http://archive.ubuntu.com jaunty-updates/universe Sources
Hit http://archive.ubuntu.com jaunty-updates/multiverse Sources
Ign http://ports.ubuntu.com jaunty/main Translation-en_US
Ign http://ports.ubuntu.com jaunty/restricted Translation-en_US
Ign http://ports.ubuntu.com jaunty/universe Translation-en_US
Ign http://ports.ubuntu.com jaunty/multiverse Translation-en_US
Hit http://ports.ubuntu.com jaunty-updates Release.gpg
Ign http://ports.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://ports.ubuntu.com jaunty-updates/multiverse Translation-en_US
Hit http://ports.ubuntu.com jaunty-security Release.gpg
Ign http://ports.ubuntu.com jaunty-security/main Translation-en_US
Ign http://ports.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://ports.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://ports.ubuntu.com jaunty-security/multiverse Translation-en_US
Hit http://ports.ubuntu.com jaunty Release
Hit http://ports.ubuntu.com jaunty-updates Release
Hit http://ports.ubuntu.com jaunty-security Release
Ign http://ports.ubuntu.com jaunty/main Packages
Ign http://ports.ubuntu.com jaunty/restricted Packages
Ign http://ports.ubuntu.com jaunty/universe Packages
Ign http://ports.ubuntu.com jaunty/multiverse Packages
Ign http://ports.ubuntu.com jaunty-updates/universe Packages
Ign http://ports.ubuntu.com jaunty-updates/multiverse Packages
Ign http://ports.ubuntu.com jaunty-security/main Packages
Ign http://ports.ubuntu.com jaunty-security/restricted Packages
Ign http://ports.ubuntu.com jaunty-security/universe Packages
Ign http://ports.ubuntu.com jaunty-security/multiverse Packages
Ign http://ports.ubuntu.com jaunty/main Packages
Ign http://ports.ubuntu.com jaunty/restricted Packages
Ign http://ports.ubuntu.com jaunty/universe Packages
Ign http://ports.ubuntu.com jaunty/multiverse Packages
Ign http://ports.ubuntu.com jaunty-updates/universe Packages
Ign http://ports.ubuntu.com jaunty-updates/multiverse Packages
Ign http://ports.ubuntu.com jaunty-security/main Packages
Ign http://ports.ubuntu.com jaunty-security/restricted Packages
Ign http://ports.ubuntu.com jaunty-security/universe Packages
Ign http://ports.ubuntu.com jaunty-security/multiverse Packages
Err http://ports.ubuntu.com jaunty/main Packages
  404 Not Found
Err http://ports.ubuntu.com jaunty/restricted Packages
  404 Not Found
Err http://ports.ubuntu.com jaunty/universe Packages
  404 Not Found
Err http://ports.ubuntu.com jaunty/multiverse Packages
  404 Not Found
Err http://ports.ubuntu.com jaunty-updates/universe Packages
  404 Not Found
Err http://ports.ubuntu.com jaunty-updates/multiverse Packages
  404 Not Found
Err http://ports.ubuntu.com jaunty-security/main Packages
  404 Not Found
Err http://ports.ubuntu.com jaunty-security/restricted Packages
  404 Not Found
Err http://ports.ubuntu.com jaunty-security/universe Packages
  404 Not Found
Err http://ports.ubuntu.com jaunty-security/multiverse Packages
  404 Not Found
W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/jaunty/main/binary-sparc/Packages  404 Not Found

W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/jaunty/restricted/binary-sparc/Packages  404 Not Found

W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/jaunty/universe/binary-sparc/Packages  404 Not Found

W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/jaunty/multiverse/binary-sparc/Packages  404 Not Found

W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/jaunty-updates/universe/binary-sparc/Packages  404 Not Found

W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/jaunty-updates/multiverse/binary-sparc/Packages  404 Not Found

W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/jaunty-security/main/binary-sparc/Packages  404 Not Found

W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/jaunty-security/restricted/binary-sparc/Packages  404 Not Found

W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/jaunty-security/universe/binary-sparc/Packages  404 Not Found

W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/jaunty-security/multiverse/binary-sparc/Packages  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


```

This my repo list or source list 
```


# 
# deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release sparc (20071016)]/ gutsy main restricted

# deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release sparc (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ports.ubuntu.com/ubuntu-ports/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
#deb http://ports.ubuntu.com/ubuntu-ports/ jaunty-updates main restricted
#deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ports.ubuntu.com/ubuntu-ports/ jaunty universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty universe
deb http://ports.ubuntu.com/ubuntu-ports/ jaunty-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ports.ubuntu.com/ubuntu-ports/ jaunty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ jaunty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://ports.ubuntu.com/ubuntu-ports/ hardy partner
# deb-src http://archive.canonical.com/ubuntu/ hardy partner

deb http://ports.ubuntu.com/ubuntu-ports/ jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://ports.ubuntu.com/ubuntu-ports/ jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu/ jaunty-security universe
deb http://ports.ubuntu.com/ubuntu-ports/ jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu/ jaunty-security multiverse

```
Please help me fix this issue this live server and i need to install some packages

---

### Post by sikander3786 on 2011-01-30
Well, you needed to update your 8.04 directly to 10.04 as 9.04 has reached End of Life is no longer supported offcially. The repositories have been shut down thats why you are getting those errors.

However, you can access the repositories as mentioned here but remember, you won't get any security updates or patches for that release.

[http://atlanticlinux.ie/blog/?p=143](http://atlanticlinux.ie/blog/?p=143)

Now, you need to upgrade 9.04 > 9.10 > 10.04 which would be a lengthy path I believe. If possible, consider a clean install with 10.04.

---

### Post by aliahsan81 on 2011-01-31
ohh thanks buddy  it solved my issue.I cant upgrade my server for now.

---

