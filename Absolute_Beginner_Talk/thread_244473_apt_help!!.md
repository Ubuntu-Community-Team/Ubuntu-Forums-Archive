---
title: "apt help!!"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by gagne on 2006-08-26
I am trying to update my box and I keep getting these Errors.I am new to Linux so I am not sure how to fix this problem.If some one can help me out that would be great.

Err [ftp://ftp.free.de](ftp://ftp.free.de) dapper/free Packages
  Unable to fetch file, server said '/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz: No such file OR directory.  '
Get:17 [ftp://ftp.free.de](ftp://ftp.free.de) dapper/non-free Packages
Err [ftp://ftp.free.de](ftp://ftp.free.de) dapper/non-free Packages
  Unable to fetch file, server said '/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz: No such file OR directory.  '
Fetched 31B in 10s (3B/s)
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/source/Sources.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/source/Sources.gz)  Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/source/Sources.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/source/Sources.gz)  Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch [ftp://ftp.free.de/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz](ftp://ftp.free.de/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz)  Unable to fetch file, server said '/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz: No such file OR directory.  '
Failed to fetch [ftp://ftp.free.de/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz](ftp://ftp.free.de/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz)  Unable to fetch file, server said '/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz: No such file OR directory.  '
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Pragmatist on 2006-08-26
> **gagne said:**
> I am trying to update my box and I keep getting these Errors.I am new to Linux so I am not sure how to fix this problem.If some one can help me out that would be great.

Err [ftp://ftp.free.de](ftp://ftp.free.de) dapper/free Packages
  Unable to fetch file, server said '/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz: No such file OR directory.  '
Get:17 [ftp://ftp.free.de](ftp://ftp.free.de) dapper/non-free Packages
Err [ftp://ftp.free.de](ftp://ftp.free.de) dapper/non-free Packages
  Unable to fetch file, server said '/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz: No such file OR directory.  '
Fetched 31B in 10s (3B/s)
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/source/Sources.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/source/Sources.gz)  Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/source/Sources.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/source/Sources.gz)  Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch [ftp://ftp.free.de/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz](ftp://ftp.free.de/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz)  Unable to fetch file, server said '/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz: No such file OR directory.  '
Failed to fetch [ftp://ftp.free.de/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz](ftp://ftp.free.de/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz)  Unable to fetch file, server said '/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz: No such file OR directory.  '
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

It looks to me like it might be a problem with your /etc/apt/sources.list file.  Follow these instructions, and see if it helps:

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

Let us know what happens.

---

### Post by Kobalt on 2006-08-26
Hi,

It seems that the repository you're trying to get a package from is closed, it's not a problem with your machine or with Aptitude. What kind of repos is this : > [ftp://ftp.free.de](ftp://ftp.free.de) dapper/free Packages ? 
What package did you install from these repos ? 

If you want to use PLF repos for Dapper I suggest you these ones : 
> ## PLF
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

Cheerios !

---

