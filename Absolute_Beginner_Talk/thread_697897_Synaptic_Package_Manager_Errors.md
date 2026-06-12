---
title: "Synaptic Package Manager Errors"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by brn on 2008-02-15
I have an older Dell laptop with Dapper that died about a year ago.  Last week before sending it off to the recycling center I tried it once more and found  it working (sort of).  A bad memory module leaves it with only 128 MB but I thought I'd keep it around anyway.  When I tried to install updates it refused.  The error message said, among other things, to run the Package Manager, which gave this report:

> E: Dynamic MMap ran out of room
E: Error occurred while processing kugar (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/
archive ubuntu.com_ubuntu_dists_dapper-updates_main_binary-i386_Packages
E: The package lists or status fle could not be parsed or opened.

W: Duplicate sources.list entry [http://http.us.debian.org](http://http.us.debian.org) stable/
main Packages (/var/lib/apt/lists/)
http.us.debian.org_debian_dists_stable_main_binary-i386_Packages

...(and other similar warnings)...

I don't think the warnings (W) are fatal but evidently the others are.  I suspect that perhaps the first line (*Dynamic MMap ran out of room*) might reflect the diminished RAM.  Can anyone say for sure?  I cannot interpret the other errors.  I looked at /var/lib/apt/lists/ and saw nothing I could identify as a problem.  I haven't been able to discover what "kugar" is or does, nor "MergeList".  In short, I'm lost.  Can anyone offer advice?

Thanks

---

### Post by aysiu on 2008-02-15
Well, you have duplicate sources. By the way, using Debian repositories in Ubuntu is not a good idea. You're better off [getting a fresh set of repositories](http://www.psychocats.net/ubuntu/sources#key).

---

### Post by brn on 2008-02-16
Tthanks Aysiu, that made it work.  apt-get update with the clean sources.list from psychocats.com shows this
> Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/dapper/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/dapper/free/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/dapper/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/dapper/non-free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/dapper/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/dapper/free/source/Sources.gz)  302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/dapper/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/dapper/non-free/source/Sources.gz)  302 Found
 which doesn't seem to impair furtther operation.

Thanks again!

---

### Post by PeterJS on 2008-02-16
Medibuntu has moved, the new setup guide is here:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

