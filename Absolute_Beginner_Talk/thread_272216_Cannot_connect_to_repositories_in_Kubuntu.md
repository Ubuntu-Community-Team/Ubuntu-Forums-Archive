---
title: "Cannot connect to repositories in Kubuntu"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by ripped_up on 2006-10-05
I cannot connect to repositories using apt-get.

when I use sudo apt-get update I get this
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 146.137.96.7 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed [IP: 146.137.96.7 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Err [http://kubuntu.org](http://kubuntu.org) dapper Release.gpg
  Connection failed
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Err [http://kubuntu.org](http://kubuntu.org) dapper Release.gpg
  Connection failed
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://kubuntu.org](http://kubuntu.org) dapper Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Ign [http://kubuntu.org](http://kubuntu.org) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Ign [http://kubuntu.org](http://kubuntu.org) dapper/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Ign [http://kubuntu.org](http://kubuntu.org) dapper/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  Connection failed
Ign [http://kubuntu.org](http://kubuntu.org) dapper/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  Connection failed
Ign [http://kubuntu.org](http://kubuntu.org) dapper/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) dapper/main Packages
  Connection failed
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
  Connection failed
Err [http://kubuntu.org](http://kubuntu.org) dapper/main Sources
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  Connection failed
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Err [http://kubuntu.org](http://kubuntu.org) dapper/main Packages
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
  Connection failed
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Err [http://kubuntu.org](http://kubuntu.org) dapper/main Sources
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
  Connection failed
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
  Connection failed
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Sources
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Packages
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Sources
  Connection failed [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Sources
  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Connection failed
Failed to fetch [http://kubuntu.org/packages/kde-latest/dists/dapper/Release.gpg](http://kubuntu.org/packages/kde-latest/dists/dapper/Release.gpg)  Connection failed
Failed to fetch [http://kubuntu.org/packages/amarok-latest/dists/dapper/Release.gpg](http://kubuntu.org/packages/amarok-latest/dists/dapper/Release.gpg)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-amd64/Packages.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-amd64/Packages.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-amd64/Packages.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-amd64/Packages.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-amd64/Packages.gz)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-amd64/Packages.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://kubuntu.org/packages/kde-latest/dists/dapper/main/binary-amd64/Packages.gz](http://kubuntu.org/packages/kde-latest/dists/dapper/main/binary-amd64/Packages.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz)  Connection failed
Failed to fetch [http://kubuntu.org/packages/kde-latest/dists/dapper/main/source/Sources.gz](http://kubuntu.org/packages/kde-latest/dists/dapper/main/source/Sources.gz)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-amd64/Packages.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://kubuntu.org/packages/amarok-latest/dists/dapper/main/binary-amd64/Packages.gz](http://kubuntu.org/packages/amarok-latest/dists/dapper/main/binary-amd64/Packages.gz)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-amd64/Packages.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://kubuntu.org/packages/amarok-latest/dists/dapper/main/source/Sources.gz](http://kubuntu.org/packages/amarok-latest/dists/dapper/main/source/Sources.gz)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-amd64/Packages.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-amd64/Packages.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-amd64/Packages.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-amd64/Packages.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/source/Sources.gz)  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/source/Sources.gz)  Connection failed [IP: 146.137.96.7 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


I have tried both the original sources.list and one I got from the net. 
My inet seems fine, Konqueror connects to webpages and ftp ok.
I am lost any help would be appreciated.

---

### Post by Marsolin on 2006-10-06
I've seen other people have this problem. Check the /etc/apt/apt.conf file and see if it has the following line. It's possible that you don't even have this file at all as it's not necessary, but it's worth a look.

Acquire::http::Proxy "false";

If it does change it to:
 
Acquire::http::DIRECT;

If that doesn't work, check and see if you have a proxy or firewall running and disable them to see if they are the problem.

If you search the forums for "connection failed" you will find other possibilities.

---

### Post by guysmiley25 on 2006-10-06
Also make sure that your dns is configured

if you can surf the web or anything should be no problem.

if not edit /etc/reslov.conf and add

nameserver <ip to DNS server>

---

### Post by ripped_up on 2006-10-06
Thanks to both of you for your help!

Marsolin that was the ticket. I changed the line to direct and it works great! Thanks!

---

