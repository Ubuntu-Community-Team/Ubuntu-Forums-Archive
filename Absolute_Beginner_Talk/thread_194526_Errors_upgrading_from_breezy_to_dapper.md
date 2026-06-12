---
title: "Errors upgrading from breezy to dapper"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by nickoli_02 on 2006-06-11
OK, I have a dapper CD that I got from a friend. I followed the instructions at [https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades) for upgrading with a CD, and I'm getting these errors:

nickoli@bob:~$ sudo apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
Identifying.. [d9f91a1075ce140463bf88837cc07be6-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes and 1 signatures
This disc is called:
'Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)'
Copying package lists...gpgv: Signature made Tue 30 May 2006 11:16:20 PM EDT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
Unmounting CD-ROM...Repeat this process for the rest of the CDs in your set.
nickoli@bob:~$ sudo apt-get update && sudo apt-get dist-upgrade
Ign cdrom://Ubuntu 5.10 _dapper drake_ - Release i386 (20051012) dapper Release.gpg
Ign cdrom://Ubuntu 5.10 _dapper drake_ - Release i386 (20051012) dapper Release
Ign cdrom://Ubuntu 5.10 _dapper drake_ - Release i386 (20051012) dapper/main Packages
Ign cdrom://Ubuntu 5.10 _dapper drake_ - Release i386 (20051012) dapper/restricted Packages
Err cdrom://Ubuntu 5.10 _dapper drake_ - Release i386 (20051012) dapper/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 5.10 _dapper drake_ - Release i386 (20051012) dapper/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper Release [34.8kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [27.0kB]
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release [27.0kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [14.4kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [14B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [3593B]
Get:10 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main Packages [619kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [14B]
Get:12 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/restricted Packages [4571B]
Get:13 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main Sources [255kB]
Get:14 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/restricted Sources [1478B]
Get:15 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/main Packages [10.2kB]
Get:16 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:17 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/main Sources [5279B]
Get:18 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Fetched 1003kB in 7s (131kB/s)
Failed to fetch cdrom:[Ubuntu 5.10 _dapper drake_ - Release i386 (20051012)]/dists/dapper/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.10 _dapper drake_ - Release i386 (20051012)]/dists/dapper/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


what do I do? :confused:

---

### Post by JanVH on 2006-06-11
Are you sure that you're use the Alternate CD, not the standard Desktop CD? It's not possible to upgrade with that one.

---

### Post by nickoli_02 on 2006-06-11
OK I downloaded the alternate CD and used that, now I just get these two errors at the very end:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

do I need to do anything about these?
Thanks for the help :-)

---

### Post by nickoli_02 on 2006-06-11
OK nvm, I fixed it :)

---

