---
title: "Updating Fails with Connection Reset?"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by caffienefree on 2007-06-06
When executing the command sudo apt-get update, I receive the following errors. Updating has worked in the past. I am trying to update over an SSH connection.

> Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.8 80]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Get:3 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg
  Error reading from server - read (104 Connection reset by peer)
Get:4 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg [189B]
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg
  Error reading from server - read (104 Connection reset by peer) [IP: 88.191.42.241 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
  Error reading from server - read (104 Connection reset by peer)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.8 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_US
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Translation-en_US
  Error reading from server - read (104 Connection reset by peer) [IP: 88.191.42.241 80]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.8 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release.gpg
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.8 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Translation-en_US
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.8 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
  Error reading from server - read (104 Connection reset by peer)
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages [6350B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages [14.0kB]
72% [7 Packages bzip2 0] [Waiting for headers] [Connecting to security.ubuntu.c
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
  Sub-process bzip2 returned an error code (2)
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages [7866B]
79% [8 Packages gzip 0] [Connecting to us.archive.ubuntu.com (91.189.89.8)] [Wa
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
  Sub-process gzip returned an error code (1)
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages [3378B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages [6402B]
76% [10 Packages gzip 0] [Waiting for headers] [Connecting to security.ubuntu.c
gzip: stdin: not in gzip format
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
  Sub-process gzip returned an error code (1)
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages [4912kB]
99% [Waiting for headers] [Waiting for headers]
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
  Sub-process gzip returned an error code (1)
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages [3181B]
99% [Waiting for headers] [Waiting for headers]
gzip: stdin: not in gzip format
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
  Sub-process gzip returned an error code (1)
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages [193kB]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.8 80]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages
Fetched 1887B in 8s (228B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg)  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg)  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/Release.gpg)  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.8 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/Release.gpg](http://medibuntu.sos-sts.com/repo/dists/feisty/Release.gpg)  Error reading from server - read (104 Connection reset by peer) [IP: 88.191.42.241 80]
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/i18n/Translation-en_US.bz2](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer) [IP: 88.191.42.241 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.8 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


I'm not sure how to interpret this. Can someone please advise me as to the meaning?

---

### Post by turinglabs on 2007-06-06
The 'connection reset by peer' means that for some reason the update server (or a firewall between you and it) is closing your connection abruptly. Try some different repositories - an easy way would be to replace every occurrence of 'http' with 'ftp' in /etc/apt/sources.list, but you could slo try a different country's servers. Then try to re-run the update.

---

### Post by ForgivenByJC on 2008-05-29
Hello, I had a very similar problem.  The issue turned out to be DansGuardian on my IPCop Firewall.  By putting ubuntu.com and canonical.com into the "Exception site (domain) list file" under Services->Content Filter page on IPCop Firewall I was able to resolve this problem.  Do not confuse "Exception site (domain) list file" with "Exception URL list file," as this will not work for this fix.  Also, research which servers are being used under System->Administration->Software Sources on your Ubuntu computer, if you are using something other than ubuntu.com (like I am using duke.edu) than also put that domain into the "Exception site (domain) list file" on your IPCop Firewall.  Mine currently has these exceptions for this problem in "Exception site (domain) list file" on my IPCop Firewall.
```
duke.edu
ubuntu.com
canonical.com
```
Good luck,
John

---

