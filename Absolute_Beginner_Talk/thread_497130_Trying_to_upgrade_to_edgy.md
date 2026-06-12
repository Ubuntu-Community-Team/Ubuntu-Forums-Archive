---
title: "Trying to upgrade to edgy"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by dittyman1 on 2007-07-09
I typed in the following command in the terminal:

*gksu "update-manager -c"*

I got the following error message:

"A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry."

Also I received this in the message.

Failed to fetch [http://www.beerorkid.com/compiz/dists/dapper/Release.gpg](http://www.beerorkid.com/compiz/dists/dapper/Release.gpg) The HTTP server sent an invalid reply header
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz](http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz) 301 Moved Permanently
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/source/Sources.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/source/Sources.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/source/Sources.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/source/Sources.gz) 404 Not Found
Failed to fetch [http://www.beerorkid.com/compiz/dists/dapper/main/binary-i386/Packages.gz](http://www.beerorkid.com/compiz/dists/dapper/main/binary-i386/Packages.gz) Bad header line

If I have a network problem, which is possible since my system is using a wireless card to access the internet, is there a better way of updating my OS?

---

### Post by linuxwizard on 2007-07-09
Remove or disable any extra repositories that may have been added besides the Ubuntu repositories. Than try again  gksu "update-manager -c"


I maybe wrong but those errors looks like from added repositories.

---

### Post by dittyman1 on 2007-07-10
OK.  Thanks.

---

