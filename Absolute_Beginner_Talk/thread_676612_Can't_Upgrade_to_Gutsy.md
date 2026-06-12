---
title: "Can't Upgrade to Gutsy"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by jo3lap on 2008-01-23
When I try to upgrade to Gutsy, an error occurs stating:

"Error during update

"A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

"Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 404 Not Found"

For some reason when I attempted to upgrade again while typing this the same error occurred but the ending of each line read "302 Moved Temporarily" instead of "404 Not Found".

Can you help me understand what's happening and what I can do to fix the problem and upgrade to Gutsy?

---

### Post by PeterJS on 2008-01-23
The medibuntu repositories have moved, try disabling the old repositories, and trying again.

After you get upgraded instructions for using the new medibuntu repository here:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

