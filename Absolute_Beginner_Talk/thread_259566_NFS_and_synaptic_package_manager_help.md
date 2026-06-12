---
title: "NFS and synaptic package manager help"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by cinderella on 2006-09-17
I'm very new to linux!! please help

I'm trying to install the nfs-kernel-server package manually from this site
*[http://packages.ubuntulinux.org/dapper/net/](http://packages.ubuntulinux.org/dapper/net/)*


however i found out that it has a depency which is the nfs-common. So i tried to install this version of nfs-common: nfs-common (1:1.0.7-3ubuntu2) from the same site (*[http://packages.ubuntulinux.org/dapper/net/nfs-common](http://packages.ubuntulinux.org/dapper/net/nfs-common)*) however I found out that it also had some depencies so i installed those as well. But when I eventually tried to install the nfs-common it gave the following error in the status bar of the package installer:

[COLOR="Lime"]Error: Conflicts with the installed package 'nfs-common'[/COLOR]
 :roll: :roll: 

how do I solve this problem???

also when I click on the [COLOR="Red"]RELOAD[/COLOR] button in the synaptic package manager I get the following errors: 

[COLOR="Lime"]http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz: 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:) 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:) 407 Proxy Authentication Required
[http://za.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://za.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://za.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:) 407 Proxy Authentication Required
[http://za.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:) 407 Proxy Authentication Required
[http://za.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://za.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://za.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://za.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://za.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:) 407 Proxy Authentication Required
[http://za.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:) 407 Proxy Authentication Required
[http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:) 407 Proxy Authentication Required[/COLOR]


how do i solve this problem!!!
:roll:

---

### Post by bluefrog on 2006-09-20
apparently you are behind a proxy.

system > preferences > proxy (or administration > proxy)
and fill in appropraite information of your network proxy

James

---

