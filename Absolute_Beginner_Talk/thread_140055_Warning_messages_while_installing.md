---
title: "Warning messages while installing"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by utab on 2006-03-05
Dear all,

When I try to install some programs I get this warning

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

The programs I installed work but I am curious about this problem(warning). I guess it is related to universe packages or am I wrong?

How to fix that?

I have pasted my sources.list file as well:

#deb cdrom:[Ubuntu 6.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse


Thx.

---

### Post by utab on 2006-03-05
[QUOTE=utab]Dear all,

When I try to install some programs I get this warning

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

The programs I installed work but I am curious about this problem(warning). I guess it is related to universe packages or am I wrong?

How to fix that?

[/QUOTE]
When try to update this is the outcome(I am sorry for the length)

Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [27.0kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release [30.9kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [30.9kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [40.8kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [19.6kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4458B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [12.3kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
67% [12 Sources bzip2 0] [Connecting to archive.ubuntu.com (82.211.81.151)] [Connecting to security.ubuntu.com (82.211.81.138)]
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
  Sub-process bzip2 returned an error code (2)
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [28.5kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources [1454B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [4747B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4055B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
73% [16 Packages gzip 0] [Waiting for headers]                                                                                                                  23.1kB/s 2s
gzip: stdin: not in gzip format
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
  Sub-process gzip returned an error code (1)
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages [31.3kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages [14B]
63% [Connecting to archive.ubuntu.com (82.211.81.151)]                                                                                                          23.1kB/s 3s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
  Sub-process bzip2 returned an error code (2)
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [15.7kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages [14.0kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages [14B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages [26.1kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages [1353B]
51% [24 Packages bzip2 0] [Connecting to archive.ubuntu.com (82.211.81.151)]                                                                                   657B/s 3m36s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
  Sub-process bzip2 returned an error code (2)
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages [767kB]
86% [25 Packages gzip 0] [Connecting to archive.ubuntu.com (82.211.81.151)]                                                                                    657B/s 3m36s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
  Sub-process gzip returned an error code (1)
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources [305kB]
89% [Working]                                                                                                                                                  657B/s 3m36s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
  Sub-process gzip returned an error code (1)
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages [3028kB]
96% [Connecting to archive.ubuntu.com (82.211.81.151)]                                                                                                         657B/s 3m36s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
  Sub-process gzip returned an error code (1)
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources [1223kB]
97% [Working]                                                                                                                                                  657B/s 3m36s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
  Sub-process gzip returned an error code (1)
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages [116kB]
97% [Connecting to archive.ubuntu.com (82.211.81.151)]                                                                                                         657B/s 3m36s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
  Sub-process gzip returned an error code (1)
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources [58.0kB]
97% [Working]                                                                                                                                                  657B/s 3m36s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
  Sub-process gzip returned an error code (1)
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages [38.1kB]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
  Error reading from server - read (104 Connection reset by peer) [IP: 82.211.81.151 80]
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [19.0kB]
96% [Connecting to archive.ubuntu.com (82.211.81.151)]                                                                                                         657B/s 4m34s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
  Sub-process gzip returned an error code (1)
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources [20B]
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages [14.4kB]
96% [34 Packages gzip 0] [Connecting to archive.ubuntu.com (82.211.81.151)]                                                                                    657B/s 4m34s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
  Sub-process gzip returned an error code (1)
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages [20B]
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages [29.3kB]
96% [Working]                                                                                                                                                  657B/s 4m34s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
  Sub-process gzip returned an error code (1)
Fetched 141kB in 18s (7610B/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz)  Error reading from server - read (104 Connection reset by peer) [IP: 82.211.81.151 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

I have pasted my sources.list file as well:

#deb cdrom:[Ubuntu 6.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse


Thx.

---

