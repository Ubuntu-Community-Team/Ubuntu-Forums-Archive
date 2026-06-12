---
title: "help help help!!! nfs insallation driving me crazy!!!"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by cinderella on 2006-09-24
hi. i'm currently using ubuntu 6.06 lts version and the packages required for the nfs-kernel-server does not exist in my synaptic manager so I went to 
[http://packages.ubuntu.com/dapper/net/](http://packages.ubuntu.com/dapper/net/)  in order to find the package and its dependacies.

Since my synaptic manager does not work properly I download each package manually. These are the packages I downloaded:

1) libevent1_1.1a-1_i386.deb
2) libnfsidmap1_0.8-1_i386.deb
3) portmap_5-16ubuntu2_i386.deb
4) nfs-common_1.0.7-3ubuntu2_i386.deb
5) nfs-kernel-server_1.0.9-2ubuntu_i386.deb

The first 3 installed without any problems but when I tried to instal nfs-common package the following error showed:

[COLOR="Red"]Error: Conflicts with the installed package 'nfs-common'[/COLOR]

hence I cannot proceed to install the nfs-kernel-server package because an error shows:
[COLOR="Red"]Error dependancy is not satisfiable[/COLOR]

](*,)

---

### Post by petri on 2006-09-24
There is also a pretty nice howto at [http://nfs.sourceforge.net/nfs-howto/index.html](http://nfs.sourceforge.net/nfs-howto/index.html)

Lots of text but it took just 15 min to get it working for a newbie, me.

Why isn't your Synaptic working?

---

### Post by cinderella on 2006-09-24
This is my problem with synaptic package manager when i click on the RELOAD button this is what happens:

[http://za.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required
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
[http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:) 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:) 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:) 407 Proxy Authentication Required



Apparently i'm behind another proxy but I dont know how to solve this!!

---

### Post by cinderella on 2006-09-24
> **petri said:**
> There is also a pretty nice howto at [http://nfs.sourceforge.net/nfs-howto/index.html](http://nfs.sourceforge.net/nfs-howto/index.html)

Lots of text but it took just 15 min to get it working for a newbie, me.

Why isn't your Synaptic working?

my actual problem is installing the nfs-common. The how-to explains what to do once the nfs-kernel-server is succesfully installed. So how do I install the nfs-common without getting any errors.

Also how do I know what version of NFS I am installing

---

### Post by petri on 2006-09-24
Another proxy? Have you chanced **to** proxy in Synaptic? Maybe you should try without proxy. I really don't know. :|

---

