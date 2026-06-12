---
title: "Connection Problems"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by chaoticnoise on 2006-10-14
Hi,
After hardly installing Ubuntu because of the Jmicron SATA controller now i am having different problems with network.The ethernet device is ok,i can also log in to the admin panel of the router,also with some changes on Firefox now i am also able to surf.But i cant log with Gaim,or the software update behaves like i have no internet connection?How can i fix that problem?

Thanks all..

---

### Post by jorn on 2006-10-14
Welcome!
What is the output of (paste in terminal:
> sudo apt-get update

---

### Post by chaoticnoise on 2006-10-14
0% [Connecting to tr.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)] :(

only this and not counting.. 

But as far i changed some values about Firefox:

(turning off ipv6 in Firefox as follows:

Enter about:config in the ff address field.

Enter ipv6 in the new Filter: field.

Now double click on the one & only line left in the display window of ff, to change it's boolean value to true.) and later firefox got the connection..But still not with Gaim,Evolution or Update...

---

### Post by chaoticnoise on 2006-10-14
Also got that output now:

Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  404 Not Found
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  404 Not Found
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
  404 Not Found
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-updates/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
  404 Not Found
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-updates/main Sources
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-updates/restricted Sources
Err [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper/main Packages
  404 Not Found
Err [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper/restricted Packages
  404 Not Found
Err [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper/main Sources
  404 Not Found
Err [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper/restricted Sources
  404 Not Found
Err [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-updates/main Packages
  404 Not Found
Err [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-updates/restricted Packages
  404 Not Found
Err [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-updates/main Sources
  404 Not Found
Err [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-updates/restricted Sources
  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://tr.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://tr.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://tr.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz](http://tr.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://tr.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://tr.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://tr.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz](http://tr.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
chaotic@Chaotic-linux:~$

---

### Post by chaoticnoise on 2006-10-15
Any ideas??

---

