---
title: "package MD5SUM mismatches"
date: 2005-07-14
forum: Apple PPC Users
---

### Post by eduardgrebe on 2005-07-14
I've been getting MD5sum mismatches on packages downloaded from archive.ubuntu.com and from various mirrors, including za.archive.ubuntu.com and uk.archive.ubuntu.com.

For example,

The following NEW packages will be installed:
  minicom
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 290kB of archives.
After unpacking 938kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main minicom 2.1-8 [290kB]
Fetched 289kB in 17s (16.2kB/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/m/minicom/minicom_2.1-8_powerpc.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/m/minicom/minicom_2.1-8_powerpc.deb)  MD5Sum mismatch

I get the problem from different mirrors, and using different internet connections.

Has anyone else had this problem?

Thanx

---

### Post by Vargis on 2005-07-14
It appears the US archives are down again.  You can delete the "us" part from the URL

See also the posting here:

[http://www.ubuntuforums.org/showthread.php?t=48691&highlight=md5sum+mismatch](http://www.ubuntuforums.org/showthread.php?t=48691&highlight=md5sum+mismatch)

---

